@Library('oremjtest') _

pipeline {
  agent any
  options {
    ansiColor('xterm')
    timestamps()
    timeout(time: 5, unit: 'MINUTES')
  }
  environment {
    PYTEST_ADDOPTS = "-n=10 --color=yes"
    PULSE = credentials('PULSE')
  }
  stages {
    stage('Test') {
      steps {
          sh "true"
      }
      post {
        always {
          threadLeak()
        }
      }
    }
  }
  post {
    failure {
        sh "echo fail"
    }
    changed {
        sh "echo changed"
      // ircNotification('#snippets')
      // ircNotification('#fx-test-alerts')
    }
  }
}
