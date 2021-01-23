# azureVPN
Deploy a Wireguard + Pi-hole server on Ubuntu Virtual Machine on Azure

## About Pi-hole
The Pi-hole is a DNS sinkhole that protects your devices from unwanted content, without installing any client-side software. You can read more about it [here](https://docs.pi-hole.net/).

## Installation Process
First we will need to set up a virtual machine.
Login to your Azure account on the [Azure portal](https://portal.azure.com).

### Setting Up Virual Machine

If you're lazy just click the button below:

![Deploy to Azure](https://aka.ms/deploytoazurebutton)

1. Click on 'Create a resource' and select Ubuntu Server 18.04 LTS.
2. Basic setup:

    ![Basic setup](/images/basics.png)
    * In **Resource group** select or create a group. It will contain every file related to your vm.
    * Give your vm a name in **Virtual machine name**.
    * In **Region** select a server location. Servers at East US have lowest pricing/hr (as of now). You might also want to check [Internet Freedom list](https://www.statista.com/statistics/272533/degree-of-internet-freedom-in-selected-countries/) while choosing server location.
    * **Size**: Select the one which matches your need. If you intend to connect ~10 devices, selcting Standard_B1ls plan with 0.5 GB of RAM and 1 vcpu will be sufficient one. However you can change this later as per your needs.
    * In **Authetication type** select SSH public key and then put a **Username**.
    * For our VPN to work properly, we need to **Select inbound ports**, choose HTTP, HTTPS and SSH.
    * Click **Next : Disks**.
3. Nothing to change here. Click **Next : Networking**
4. To connect to our VPN and to see Pi-hole stats, we will need a static IP. Click **Create new** under **Public IP**. Now select **Static** in **Assignment**.

    ![Create public IP address](/images/networking.png)
5. Now click **Next : Management**.
6. Make sure that **Auto-shutdown** is left unchecked.
7. Now click **Review + create** button.