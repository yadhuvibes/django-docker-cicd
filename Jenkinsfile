pipeline {
agent any

stages {
    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t django-app .'
        }
    }

    stage('Stop Old Container') {
        steps {
            sh 'docker stop django-container || true'
            sh 'docker rm django-container || true'
        }
    }

    stage('Run Container') {
        steps {
            sh 'docker run -d --name django-container -p 8000:8000 django-app'
        }
    }

    stage('Verify') {
        steps {
            sh 'docker ps'
        }
    }
}

}

