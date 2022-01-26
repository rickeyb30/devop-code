pipeline {
  agent any
  tools {
     maven 'M2_HOME'
  }
  environment{
  registry = "rickeyb30/devop-pipeline"
  registryCredential = 'DockerID'
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
      }
    } 
    stage ('Test') {
      steps {
      echo "test steps"
      sh 'mvn test'
     }
    } 
    stage ('Deploy') {
      steps {
        script {
        docker.build registry + ":$BUILD_NUMBER"
        }
      }
    } 
  }
