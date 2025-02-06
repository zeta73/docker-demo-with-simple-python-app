pipeline {
    agent any

    environment {
        DOCKER_REGISTRY = 'registry-intl.ap-southeast-5.aliyuncs.com'
        DOCKER_NAMESPACE = 'gandes-test'
        IMAGE_NAME = 'build-from-jenkins'
        IMAGE_TAG = '2.0'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/zeta73/docker-demo-with-simple-python-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${DOCKER_REGISTRY}/${DOCKER_NAMESPACE}/${IMAGE_NAME}:${IMAGE_TAG} ."
                }
            }
        }

        stage('Push to ACR') {
            steps {
                script {
                        sh "echo 'R4h4s1ah2017&*' | docker login --username=ryan@testindonet --password-stdin registry-intl.ap-southeast-5.aliyuncs.com"
                        sh "docker push ${DOCKER_REGISTRY}/${DOCKER_NAMESPACE}/${IMAGE_NAME}:${IMAGE_TAG}"
                    }
                }
            }
        }
    }
