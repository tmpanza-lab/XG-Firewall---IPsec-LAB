# XG Firewall | IPsec LAB

## Objective

The main objective of this Sophos XG Firewall IPsec LAB is to establish a secure site-to-site VPN tunnel using IPsec between two geographically separated networks (Site A and Site B). This setup allows seamless communication between the local networks (`192.168.2.0/24` at Site A and `192.168.50.0/24` at Site B) over an encrypted connection through the internet.

### Job Skills Learned

- Basic Sophos XG Firewall Administration Skill
- Configuring an IPsec VPN tunnel between Sophos XG Firewalls at two different sites.
- Verify VPN tunnel status, debug connection issues
- Understanding Network Segmentation & Routing
- Configuring Firewall Rules
- Implementing NAT and Routing Policies
- Testing and Validating Firewall & Security Policies


### Tools Used

- Sophos XG Firewall VM: A virtual appliance used in virtualized environments (VMware).
- SFOS 17.5 Web Interface (GUI)
- SFOS 17.5 Command Line Interface (CLI)
- Control Center Dashboard: Built-in monitoring tool for real-time traffic and event analysis.
- Backup and Restore Tools
- Traffic Generation Tools
- EVE-NG for simulating network devices (e.g., routers, PCs, or switches) to test


*Ref 1: Network Diagram*
 ![image](https://github.com/user-attachments/assets/224c6be6-bb60-48e4-ab83-ea9e3974d067)

### IPsec Ports & Protocols
- Protocol: UDP, port `500` (for IKE, to manage encryption keys)
- Protocol: UDP, port `4500` (for IPSEC NAT-Traversal mode)
- Protocol: ESP, value `50` (for IPSEC)
- Protocol: AH, value `51` (for IPSEC)

### STEPS

### IPsec Tunnel Configuration Table:
- Parameter	XG-Site A (Head Office)	XG-Site B (Branch Office)
- Gateway Address	`192.168.8.199`	`192.168.18.254`
- Local Network	`192.168.2.0/24`	`192.168.50.0/24`
- Remote Network	`192.168.50.0/24`	`192.168.2.0/24`
- Local ID	`192.168.8.254`	`192.168.8.199`
- Remote ID	`192.168.8.199`	`192.168.8.254`



## Steps to Configure IPsec Tunnel:
1.	- Create IPsec Tunnel – Using Wizard or Manually (Both Sides).
![image](https://github.com/user-attachments/assets/6de67929-fc93-4cfc-9c46-1b6384076150)
 
Via the Wizard
![image](https://github.com/user-attachments/assets/c8699485-f6c2-4e4a-a494-3b4d1bf251d4)
 


*Remote access connection is established to connect individual hosts to access a private network over the internet without a static IP address

*Site-to-site connection is established to connect two networks over the internet. For example, connecting a branch office network to a company's head office network.

*Host-to-host connection established secure tunnel between two hosts
![image](https://github.com/user-attachments/assets/a64012ac-00b5-4bf6-9bc8-a93a3178a63d)

 

These are all the policies 
![image](https://github.com/user-attachments/assets/f7868c22-323e-4a66-abdb-6c4b941e9b67)
 
Actions
![image](https://github.com/user-attachments/assets/4a108bfa-74fb-4d92-bc45-131439b70bb9)
 

Preshared key Authenticate IPsec endpoints by using the secret know to both the endpoints
![image](https://github.com/user-attachments/assets/0a37c207-b8dd-45a9-9c3b-62230f364a6f)
 
Local server will allow you to select the WAN port, which acts as the endpoint for your tunnel
![image](https://github.com/user-attachments/assets/f827c851-7ab1-4f06-ad77-f870b9733f5d)
 
Public IP address of Site_B
![image](https://github.com/user-attachments/assets/fe5c0d85-b47a-402f-a300-0a85b47109f9)
![image](https://github.com/user-attachments/assets/ee6be57b-d9ce-454c-8005-784cdfd2e189)
 
 
Finish – Current status it’s showing down (red)
![image](https://github.com/user-attachments/assets/d17358b5-8034-45c8-8dcc-8c8584486ab7)
 


These are the details available
![image](https://github.com/user-attachments/assets/2b8b1efe-5133-4d30-bf8e-3598fa3305ca)
![image](https://github.com/user-attachments/assets/057c3da2-d1ab-434c-858c-a1337c2e4dcb)
 
 

### SiteB
![image](https://github.com/user-attachments/assets/b27e579f-069a-4587-a3ce-f500c1c74521)
 

This is my Branch Office, Head Office will Respond Only and Branch will Initiate
![image](https://github.com/user-attachments/assets/834a7bf7-de87-4e68-8b37-c06081da5c9c)
 
Provide same Preshared key
![image](https://github.com/user-attachments/assets/8786ed84-6cad-4d6b-ad0c-df02f56d090d)
 
Local Network details
![image](https://github.com/user-attachments/assets/8ecfb81f-656b-465f-afa8-ecf2864671b1)

 
Remote Network details
![image](https://github.com/user-attachments/assets/b366a06a-c9c3-477a-a65a-bfc550acc127)
 
IPsec connection summary
![image](https://github.com/user-attachments/assets/34296e31-6072-46ef-a6bb-b94c13dcf562)
 


2.	- Create Two Firewall Rules – LAN-VPN & VPN-LAN (Both Sides).
Site A – Head Office
![image](https://github.com/user-attachments/assets/296e9a29-2c8d-4311-b680-17a810e43559)
![image](https://github.com/user-attachments/assets/6c30b98d-9646-457a-8423-6ae88c42b827)
![image](https://github.com/user-attachments/assets/85300bc0-6356-4bfc-a6ee-efe37eed3f9d)
 
 
 
Rule has been created
![image](https://github.com/user-attachments/assets/c53855a8-19d6-49b4-a39b-715a22d8dd88)
 
We need another rule for traffic from VPN to LAN
![image](https://github.com/user-attachments/assets/eddf8c30-e921-4d81-a88e-f1cfc885e8cc)
![image](https://github.com/user-attachments/assets/1ea2b6aa-21bf-40bf-b470-062efdb9e484)
![image](https://github.com/user-attachments/assets/ab3e5655-f3bd-4256-9668-942cbf48549c)
 
Destination 
![image](https://github.com/user-attachments/assets/d1629433-6828-4840-9157-1e64003a7836)
![image](https://github.com/user-attachments/assets/cdeb5feb-be27-4983-827d-3811c227603c)
 
 
So we have created two firewall rules here on the Head Office site A
![image](https://github.com/user-attachments/assets/6d623b16-3a5e-4691-ac2f-b5f824c15b46)
 
So we need the same for our Branch Office site B
![image](https://github.com/user-attachments/assets/f3cd2cd3-12aa-4ba8-a7bc-6e3e9cbc11b1)
 
Destination 
![image](https://github.com/user-attachments/assets/dd2d25d0-21b5-49e7-9a3f-00bb3e50c343)
![image](https://github.com/user-attachments/assets/bd869b98-deb1-49b3-8559-bd99eb712053)
 
 
Source zone
![image](https://github.com/user-attachments/assets/df5979a4-dfb8-4d03-88a8-9927959ca941)
 
Destination
![image](https://github.com/user-attachments/assets/da92ab32-40d8-42da-8dc9-fe26745c77ae)
 



3.	- Enable Ping in VPN Zone.

I need to activate this connection from Head Office Site A
![image](https://github.com/user-attachments/assets/77892ffa-3f62-4e24-b3d2-bd1a7da298a2)
![image](https://github.com/user-attachments/assets/3058a318-935d-4f7f-af8e-0a76d04e0be5)
 
I need to activate this connection from Branch Office Site B remote site also
![image](https://github.com/user-attachments/assets/69629c81-8479-4955-8286-2588cfb8a93f)
![image](https://github.com/user-attachments/assets/765e196f-4e9d-4191-8f97-f0ddf856fe5b)
 
 
Tunnel has been established (IPsec Tunnel) from both sides.
![image](https://github.com/user-attachments/assets/c55f5adc-704f-40cd-b3a9-23815d842d4d)
![image](https://github.com/user-attachments/assets/857fb6fe-5b1e-47e1-b29f-8649484fff30)
 
 
Enable ping for VPN
![image](https://github.com/user-attachments/assets/ad801aca-d997-45da-a97d-18645c5d66f2)
 

4.	- Check the Connectivity.
Accounts PC IP settings
![image](https://github.com/user-attachments/assets/1eaffe9a-b69e-47b1-ad6c-40fcb06c901c)
 
Remote Site B
![image](https://github.com/user-attachments/assets/19fc98f1-0be5-4aef-8747-8943c7750bd6)
 
We are getting reply from Head Office 
![image](https://github.com/user-attachments/assets/e7421c04-12d5-4941-9a3f-dffe1e67de96)
 
Branch PC is also responding when we ping it from the Head Office
![image](https://github.com/user-attachments/assets/46fc6164-99eb-4d68-b788-562beea05a0e)
 
Route Lookup
![image](https://github.com/user-attachments/assets/a1aab507-48e5-4c63-a3c9-a7f109bb48df)
 
CLI command ``` ipsec statusall ```
![image](https://github.com/user-attachments/assets/3934843f-0542-49ee-882d-45c832805537)

CLI command ``` tail -f /log/strongswan.log ```
![image](https://github.com/user-attachments/assets/57cbe302-991b-4a2e-ba6f-e96f1c5a8aa1)
![image](https://github.com/user-attachments/assets/70ae6260-bdf5-4c3e-974a-99c58f102ea0)
 
________________________________________

IPsec Tunnel will be established between Two Peers & to establish an IPsec tunnel, we use a protocol called IKE (Internet Key Exchange).
There are two phases to build an IPsec tunnel:
- IKE phase 1
- IKE phase 2

- IKE phase 1
![image](https://github.com/user-attachments/assets/36563c18-f433-4aa9-8d2d-81304ca5e275)

- IKE phase 2
 ![image](https://github.com/user-attachments/assets/1dcabf7a-97ee-4d21-bfb1-71f541967ea7)

Once IKE phase 2 is completed, we have an IKE phase 2 tunnel (or IPsec tunnel) that we can use to protect our user data. This user data will be sent through the IKE phase 2 tunnel.
![image](https://github.com/user-attachments/assets/5ec3d292-05da-4a87-ae1c-83a85b042935)



## BONUS - Setup High Avalability (HA)
![image](https://github.com/user-attachments/assets/62bb26c4-5a95-40f3-9718-5fe6d85932c6)

 
Prerequisites
- Both devices in the HA cluster (that is, Primary Device and Auxiliary Device) must be the same model and revision.
- Both devices must be registered.
- Both devices must have the same number of interfaces.
- Both devices must have the same firmware version installed. This includes maintenance releases and hot-fixes as well as firmware build. You can verify the firmware version using the following console command: system diagnostics show version-info


## BONUS - Sophos Central
Sophos Central is a cloud-based cybersecurity management platform that allows IT administrators to manage and monitor various Sophos security products from a single interface. It provides centralized control over endpoint protection, firewall management, email security, mobile device management, server protection, and more.

![image](https://github.com/user-attachments/assets/0a4cf0a8-0db8-43ea-af23-4e61027327ad)

Alerts
![image](https://github.com/user-attachments/assets/4244eb0a-8a61-4567-a241-51aefb67dcd4)

Turning Off Sophos XG Firewall to test notifications.
![image](https://github.com/user-attachments/assets/8b05296b-0e5d-47c3-8ce4-4937c7d1965a)
![image](https://github.com/user-attachments/assets/8db8f2eb-7e9e-4457-bf5f-08f1354ca7b5)
![image](https://github.com/user-attachments/assets/0c106691-db29-488b-acaf-0af1112a10ab)
![image](https://github.com/user-attachments/assets/7e579c8a-8136-40a4-8f2c-b8f291e69674)
![image](https://github.com/user-attachments/assets/c6a3760f-8cd5-4f30-b979-ad1235cbb4d8)

### Bonus - Packet Capture on CLI
Command ``` 'host 192.168.3.10' ``` here I am runing a packet capture to my AD Server host machine in CLI.
![WhatsApp Image 2025-03-06 at 22 31 44_e52b19d6](https://github.com/user-attachments/assets/05a4475e-1f91-4031-bd31-5e77e33470b6)


 
 
 

 
 

 
 

 
