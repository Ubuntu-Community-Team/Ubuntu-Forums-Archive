---
title: "General thoughts"
date: 2012-08-09
forum: General Help
---

### Post by burnedfaceless on 2012-08-09
I believe people have used remote desktop viewer to access my computer. I don't see any need to delete it per se. I'm trying to learn more about ubuntu in general and how this could be accessed.

First of all how does it work protocol wise what is SSH, VNC, and RDP. I glanced at wikipedia but what are the advantages of this. How would someone be able to access information to connect to my computer?

Also would a firewall protect me from this type of connection. I understand an open port can be a weak spot but if there was a firewall would it prevent this?

Is there a need for anti virus software on Ubuntu? It seems my boot times have slowed. 

Really any information would be great. I see the use in this program especially with windows users.

---

### Post by papibe on 2012-08-09
Hi burnedfaceless. Welcome to the forums ):P

VNC (RFB protocol), and RPD are both used for graphical remote connections. SSH is a protocol for a text based connection and a very powerful tool to create secure tunnels.

VNC is not a secure protocol. RPD has been improved over the years to be a little more secure.

SSH is secure by design: the connection is encrypted, making it very useful to use not only in a LAN but over the Internet. Using the SSH's tunnelling capabilities you can securely use VNC over SSH.

All of them work in a server/client model.

In order to initiate a connection, you use the client. Most clients are installed by default and don't need much configuration.

In order to receive a connection you need to have a service running and accepting connections. Most of them are either not installed, or not set up to receive connections by default.

Does that helps a little?
Regards.

---

### Post by burnedfaceless on 2012-08-09
> **papibe said:**
> Hi burnedfaceless. Welcome to the forums ):P

VNC (RFB protocol), and RPD are both used for graphical remote connections. SSH is a protocol for a text based connection and a very powerful tool to create secure tunnels.

VNC is not a secure protocol. RPD has been improved over the years to be a little more secure.

SSH is secure by design: the connection is encrypted, making it very useful to use not only in a LAN but over the Internet. Using the SSH's tunnelling capabilities you can securely use VNC over SSH.

All of them work in a server/client model.

In order to initiate a connection, you use the client. Most clients are installed by default and don't need much configuration.

In order to receive a connection you need to have a service running and accepting connections. Most of them are either not installed, or not set up to receive connections by default.

Does that helps a little?
Regards.

That helps some. Someone pasted a message. How would I disable this type of connection and would a firewall prevent it? I'm noticing a ton of processes and my computer is running slow. I want to record music on it but I also want some privacy/people not wasting my bandwith....you get the jist.

---

### Post by papibe on 2012-08-09
To avoid VNC connections open 'Remote Desktop' and make sure that the option 'Allow other users to view your desktop' is not checked.

To make sure you don't receive ssh connections, don't install openssh-server. Run this to check if it is installed:
```
apt-cache policy openssh-server
```
In case it is installed, remote it:
```
sudo apt-get remove openssh-server
```
Regards.

---

### Post by burnedfaceless on 2012-08-10
I'm upgrading my distro so I'll run the command in a minute but would a firewall prevent these types of incoming connections?

---

