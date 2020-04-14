pipeline {
  agent any
  environment {
    INVENTORY = credentials('INVENTORY_INI')
  }
  stages {
            stage('Checkout') {
                steps {
                    checkout scm
                }
             }
            stage('Create Inventory') {
                steps {
                    sh 'echo $INVENTORY  | base64 -d > inventory.ini'
                }
            }
            stage('Docker DM storage') {
                steps {
                    sh 'ansible-playbook -i inventory.ini docker-storage-setup-ofs.yml'
            }
        }
    }
}