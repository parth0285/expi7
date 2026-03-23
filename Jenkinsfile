pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/parth0285/expi7.git'
            }
        }

        stage('Build & Test') {
            steps {
                bat 'mvn clean verify'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat '''
                    mvn sonar:sonar ^
                    -Dsonar.projectKey=demo-project ^
                    -Dsonar.host.url=http://localhost:9000 ^
                    -Dsonar.login=YOUR_TOKEN
                    '''
                }
            }
        }
    }
}
