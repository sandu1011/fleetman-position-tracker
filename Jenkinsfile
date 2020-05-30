node {
    
    stage('Preparation') {
        
        git 'https://github.com/sandu1011/fleetman-position-tracker'
    }
    stage('Build') {
        sh "mvn package"
    }
    stage('Results') {
        
        junit '**/target/surefire-reports/TEST-*.xml'
        archive 'target/*.jar'
    }
    stage('Deploy') {
        
 ansiblePlaybook credentialsId: 'ssh-credentials', installation: 'ansible-installation', playbook: 'deploy.yaml'
    }    

}
