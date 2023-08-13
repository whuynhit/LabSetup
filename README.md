# Lab Setup

This is how the lab environment for Active Directory and SCCM is setup on a host machine that runs with the following hardware specifications:</br>
- CPU - AMD Ryzen 7 3700X, virtualization enabled via BIOS/UEFI
- RAM - 32GB
- Storage - Minimum of 250GB
  - 50GB for Domain Controller
  - 50GB for Client
  - 150GB for SCCM Server

Using [VirtualBox](https://www.virtualbox.org/wiki/Downloads) from Oracle and official evaluation OS images for [Windows Server 2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022) and [Windows 10 Enterprise](https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise), three virtual machines are named as follows:

[Windows Server 2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)
  -  WS22DC - Domain Controller
  - WS22SCCM - SCCM Server

[Windows 10 Enterprise](https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise)
- Client1 - Client Endpoint under Active Directory and SCCM administration
</br>

<details>
  <summary><b>Creating VMs</b></summary>

  Create three virtual machines like so:
  <details>
  <summary>Domain Controller</summary>
    
  ![WS22DC 1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22DC/1.png)
  
  ![WS22DC 2](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22DC/2.PNG)
  
  ![WS22DC 3](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22DC/3.PNG)
  
  ![WS22DC 4](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22DC/4.PNG)
  
  </details>

  <details>
  <summary>SCCM Server</summary>
    
  ![WS22SCCM 1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22SCCM/1.PNG)
  
  ![WS22SCCM 2](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22SCCM/2.PNG)
  
  ![WS22SCCM 3](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22SCCM/3.PNG)
  
  ![WS22SCCM 4](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/WS22SCCM/4.PNG)
  
  </details>

  <details>
  <summary>Client</summary>
    
  ![Client1 1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/Client1/1.PNG)
  
  ![Client1 2](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/Client1/2.PNG)
  
  ![Client1 3](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/Client1/3.PNG)
  
  ![Client1 4](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/1%20Making%20VM/Client1/4.PNG)
  
  </details>
  
</details>

</br>

<details>
  <summary><b>VirtualBox Network settings</b></summary>
  In Virtual Box, set the 1st network adapter attached to "NAT" for the Domain Controller VM
  
  ![1st Machines](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/2%20VM%20Network%20Settings/1.PNG)

  For the 2nd network adapter on the Domain Controller, attach to "Internal Network" and name it however you wish
  ![2nd](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/2%20VM%20Network%20Settings/2.PNG)

  For the SCCM Server and Client VMs, attach the 1st network adapters to the "Internal Network" that was just created

  Both the SCCM Server and Client VMs will access the internet through the Domain Controller, with the Domain controller serving as DHCP and DNS Server
  
</details>

</br>

<details>
  <summary><b>WS22DC</b></summary>
  Mount the OS image
  
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/1.PNG) </br>
  Next
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/2.png)
  Install Now
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/3.png)
  Select Standard Evaluation (Desktop Experience)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/4.png)
  Accept license terms
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/5.png)
  Select Custom Install
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/6.png)
  Next
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/7.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/8.png)
  Using "Password1", but you may choose any simple password for lab environment
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/9.png)
  Login with "Password1"
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/10.png)
  Open Settings>Network & Internet, Select "Change adapter options" </br>
  Leave one of the network adapters to default, and rename one to "Internal" </br>
  Open properties window for the "Internal" adapter, and select Internet Protocol Version 4 </br>
  Assign it with the following:</br>
  IP address: 192.168.0.1 </br>
  Subnet mask: 255.255.255.0 </br>
  Default gateway: -blank- </br>
  Preferred DNS Server: 127.0.0.1 </br>
  Click OK
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/11.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/12.png)
  In Settings>System>About, click "Rename PC" </br>
  Rename PC so that it can be identified as a Domain Controller </br>
  Restart now </br>
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/13.png)
  Click "Add roles and features" </br>
  Next </br>
  Continue with "Role-based or feature-based Installation" </br>
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/14.png)
  Continue with currently selected server from server pool
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/15.png)
  
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/16.png)
  Select the following features: </br>
  Active Directory Domain Services </br>
  DHCP Server </br>
  DNS Server </br>
  Remote Access </br>
  </br>
  Then click Next </br>
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/17.png)
  Select "Direct Access and VPN (RAS)" and "Routing" and continue
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/18.png)
  Confirm, install, and wait for completion.
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/19.png)
  
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/20.png)
  In the Server Manager, click the flag and select "Promote this server to Domain Controller"
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/21.png)
  Select "Add a new forest" and name your root domain
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/22.png)
  Proceed with the following options as with the screenshot below and use a simple password like "Password1" for DSRM password
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/23.png)
  Make sure DNS Delegation is unchecked and click Next
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/24.png)
  Pass the prerequisites check and install
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/25.png)
  In the Server Manager, Tools > Active Directory Users and Computers </br>
  In your domain, create a new Organizational Unit (OU) </br>
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/26.png)
  
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/27.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/28.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/29.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/30.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/31.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/32.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/33.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/34.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/35.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/36.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/37.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/38.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/39.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/40.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/41.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/42.png)
  ![WS22DC](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3%20Installing%20and%20Setting%20up%20WS22DC/43.png)
    
</details>

</br>

<details>
  <summary><b>WS22SCCM</b></summary>
  Mount the OS image
  
  
</details>

</br>

<details>
  <summary><b>Client1</b></summary>
  Mount the OS image
  
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/1.PNG) </br>
  Next
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/2.png)
  Install Now
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/3.png)
  
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/4.png)
  Accept license terms
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/5.png)
  Select Custom Install
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/6.png)
  Next
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/7.png)
  
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/8.png)
  Select a region and click "Yes"
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/9.png)
  Select a keyboard layout and click "Yes"
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/10.png)
  Click "I don't have internet"
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/11.png)
  Continue with limited setup
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/12.png)
  Type in any username
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/13.png)
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/14.png)
  You may proceed without a password
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/15.png)
  You may proceed with or without changing any privacy settings
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/16.png)
  You may select "Accept" or "Not now"
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/17.png)
  Wait for set up to finish
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/18.png)
  Open Settings>System>About and clicking "Rename this PC (Advanced)" under Related Settings should open System Properties</br>
  In the System Properties window, click "Change..." should open the Computer Name/Domain Change window that will allow you to change the PC name and join the client PC to a domain using domain user/administrator credentials </br>
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/19.png)
  Success and done!
  ![Client1](https://github.com/whuynhit/LabSetup/blob/main/Lab%20Setup/3b%20Installing%20and%20Setting%20up%20Client1/20.png)
  
</details>
