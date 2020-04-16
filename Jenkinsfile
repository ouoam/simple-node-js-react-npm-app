pipeline {
  agent {
    docker {
      args '-p 3000:3000'
      image 'node:6-alpine'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        echo 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }

  }
  environment {
    CI = 'true'
  }
}