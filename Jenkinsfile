pipeline {
  environment {
    registry = “vanvoo/proj1”
    registryCredential = ‘DockerHubCredentials’
    dockerImage = ‘’
  }
  agent any
  stages {
    stage(‘Cloning’) {
      steps {
        git ‘https://github.com/vanvoo/proj1.git‘
      }
    }
    stage(‘Building image’) {
      steps{
        script {
          dockerImage = docker.build registry + “:$BUILD_NUMBER”
        }
      }
    }
    stage(‘Deploy Image’) {
      steps{
        script {
          docker.withRegistry( ‘’, registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}

