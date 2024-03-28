pipeline {
  agent any
  stages {
    stage ('Install') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'admin', path: '', url: 'http://localhost:7070/')], contextPath: '/pipeline', onFailure: false, war: 'target/*.war'
        }
      }
    }
  }
}