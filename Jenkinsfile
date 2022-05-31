@Library('shared-build-agents@main') _

pipeline {
  agent {
    kubernetes {
      yaml libraryResource('podTemplates/secure-CICD.yaml')
    }
  }
  stages {
    stage('Build My Docker Image')  {
      steps {
        container('secureCID-agent') {
            sh 'docker info'
            sh 'touch Dockerfile'
            sh 'echo "FROM centos:7" > Dockerfile'
            sh "cat Dockerfile"
            sh "docker -v"
            sh "docker info"
            sh "docker build -t my-centos:1 ."
            sh "helm version"
        }
      }
    }
  }
}
