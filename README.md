# Environment setup
## Visual Studio Code
- Download Visual Sutio Code from [here](https://code.visualstudio.com/Download)
    - install VS code on local PC
    - install extensions : CMake / CMake Tools / Remote Containers
## Azure RTOS source package
- Download Azure RTOS simulator from (?)
- Create a working directory and unzip the source package to the directory

# Set up Azure IoT Hub
- install Azure CLI tool from [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- Create Azure IoT Hub
    - > az extension add --name azure-iot
    - > az login
    - > az group create --name MyResourceGroup --location centralus
    - > az iot hub create --resource-group MyResourceGroup --name {YourIoTHubName}
- Register a device
    - > az iot hub device-identity create --device-id MySimDevice --hub-name
{YourIoTHubName}
    - After the device is created, view the JSON output in the console, and copy the deviceId and primaryKey values to use in a later step
        - hostName
        - deviceId
        - primaryKey

# Build VS Code project
- install Docker for Windows from [here](https://docs.docker.com/docker-for-windows/install/)
- launch VS Code
- File -> Open Folder -> (select project directory)
- "Reopen in container"
- set active kit "GCC for x86_64-linux-gnu-7.5.0"
- in "sample_config.h", modify
    - HOST_NAME
    - DEVICE_ID
    - DEVICE_SYMMETRIC_KEY
- Select **Build** on the bottom status bar to build the device code

# View device properties on IoT Hub
- install Azure IoT Explore from [here](https://docs.microsoft.com/en-us/azure/iot-pnp/howto-use-iot-explorer#install-azure-iot-explorer)
- Launch Azure IoT Explore
- IoT Hub -> Add Connection
- from Azure CLI command
    - > az iot hub show-connection-string --name {YourIoTHubName}
    - to get the connection string from IoT Hub
- Copy and paste the connection string to the "**Connection string**" box
- Save

# Interact with IoT Hub
- Device Identity
- Telemetry
- Device Twin
- Direct Method
- Cloud to Device
- IoT Plug and Play

