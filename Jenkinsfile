def genericSh(cmd) {
  if (isUnix()) {
    sh cmd
  }
  else {
    bat cmd
  }
}

node {
  stage('Checkout') {
    checkout scm
  }

  stage('Build') {
    azureIoTEdgePush dockerRegistryType: 'acr', acrName: 'tharak', bypassModules: '', azureCredentialsId: 'az-tharak-service-principal', resourceGroup: 'iot-hub-tharak-rg', rootPath: './'
  }

  stage('Deploy') {
    azureIoTEdgeDeploy azureCredentialsId: 'az-tharak-service-principal', deploymentId: 'jenkins-iot-pipeline', deploymentType: 'single', deviceId: 't-rpr-4', iothubName: 'iot-hub-tharak-one', priority: '0', resourceGroup: 'iot-hub-tharak-rg', rootPath: './', targetCondition: ''
  }
}