pipeline{
  agent { node { label 'awsnode' } } 
  tools {
      git 'git'
      maven 'Maven'
  }

  stages{
    stage('SCM Checkout'){
     steps{
          git 'https://github.com/mohansgithub/BookApp.git'
          }
  }

    stage('Maven packing'){
     steps{
           sh label: '', script: 'mvn clean install'
        }
    }
    stage('cleanup'){
     steps{
           deploy adapters: [tomcat9(credentialsId: 'c6f38fc0-801b-44b3-aac3-36a5d8a65b4e', path: '', url: 'http://65.0.173.129:8080')], contextPath: 'BookApp', war: '**/*.war'
        }
    }
  }
}
