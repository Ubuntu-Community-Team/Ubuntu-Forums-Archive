---
title: "Ubuntu 10.04.1 LTS Server Not Recognizing sshd_config"
date: 2012-03-22
forum: General Help
---

### Post by The8thLegion on 2012-03-22
I have two xenforo forums on shared hosting and want to switch one of them to VPS. I recently bought an unmanaged vps server from [www.fanaticalvps.com]("http://www.fanaticalvps.com") and their default server was CentOS 5. They had several options to install a new server so I chose Ubuntu 10.04 LTS 32-bit. Since I am a noob to this server stuff I've been google searching guides. This is what I've done so far.

I am unable to login using my old root password so after installing Ubuntu, I reset the password from their SolusVM Access Panel.

I open up putty and login as root using the new password.

I then enter these commands:


apt-get update && apt-get upgrade 

apt-get install nano

adduser myusername


Then I go to visudo 
myusername ALL=(ALL) ALL
at the bottom of the visudo file.


Another guide said to do this:
addgroup sshlogin

adduser myusername sshlogin

AllowGroups sshlogin 

Now no changes in my /etc/ssh/sshd_config folder seem to work.

Did my problem begin because I reset the root password? What is the default password after installing Ubuntu? I don't install Ubuntu, I select the option and the server automatically installs it. I feel like I'm missing something. All I know is that it won't save any edits that I make to the sshd_config file.

Edits such as:

PermitLogin no
Port (a port different than 22 like 41111 for example)

---

### Post by azmyth on 2012-03-22
How did you edit the sshd_config file?

sudo nano /etc/ssh/sshd_config

Is the correct way.

Also, you must restart ssh every time you change the file in order for the changes to take effect.

---

### Post by The8thLegion on 2012-03-22
> **azmyth said:**
> How did you edit the sshd_config file?

sudo nano /etc/ssh/sshd_config

Is the correct way.

Also, you must restart ssh every time you change the file in order for the changes to take effect.I did not restart ssh. K. I'm just gonna reinstall 10.04 and start all over from the beginning.

---

### Post by The8thLegion on 2012-03-22
brb

---

### Post by The8thLegion on 2012-03-22
> **azmyth said:**
> How did you edit the sshd_config file?

sudo nano /etc/ssh/sshd_config

Is the correct way.

Also, you must restart ssh every time you change the file in order for the changes to take effect.It worked, thank you!

---

### Post by The8thLegion on 2012-03-22
I am following [The Perfect Server]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p3") guide. It says to open /etc/network/interfaces and configure the network.

> 
**7 Configure The Network**

Because the Ubuntu installer has configured our system to get its  network settings via DHCP, we have to change that now because a server  should have a static IP address. Edit */etc/network/interfaces * and adjust it to your needs (in this example setup I will use the IP address *192.168.0.100*): 



```
# This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).  # The loopback network interface auto lo iface lo inet loopback  
# The primary network interface
auto eth0
iface eth0 inet static   
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```
^^^Unfortunately, their example varies greatly from mine. 

My file says I can't edit it and does not show a section that says 'The Primary Network Interface'. 

This is what my file says:

```

# Please create/edit /etc/network/interfaces.head and
# /etc/network/interfaces.tail instead, their contents will be
# inserted at the beginning and at the end of this file, respectively.
#
# NOTE: it is NOT guaranteed that the contents of /etc/network/interfaces.tail
# will be at the very end of this file.
#

# Auto generated lo interface
auto lo
iface lo inet loopback

# Auto generated venet0 interface
auto venet0
iface venet0 inet manual
        up ifconfig venet0 up
        up ifconfig venet0 127.0.0.2
        up route add default dev venet0
        down route del default dev venet0
        down ifconfig venet0 down


iface venet0 inet6 manual
                                
 up ifconfig venet0 add 2abunch:of:numbers:8
 down ifconfig venet0 del 2abunch:of:numbers:7
 up route -A inet6 add default dev venet0
 down route -A inet6 del default dev venet0

auto venet0:0
iface venet0:0 inet static
        address my.servers.ip.address
        netmask 255.255.255.255
```How would I edit this properly according to the guide?

---

### Post by azmyth on 2012-03-22
I'm surely no expert but I don't think it would be wise to edit this file as you have a vps guest and this file is needed to communicate with the VPS server properly. Your guide is just wanting to setup a static IP so the IP doesn't change. I'm sure your vps is already set for this.

---

### Post by The8thLegion on 2012-03-23
> **azmyth said:**
> I'm surely no expert but I don't think it would be wise to edit this file as you have a vps guest and this file is needed to communicate with the VPS server properly. Your guide is just wanting to setup a static IP so the IP doesn't change. I'm sure your vps is already set for this.
Oh okay thank you! Please mark this thread solved since my issue in the first post was resolved.

I created a different topic since this is a different issue from the thread title: [http://ubuntuforums.org/showthread.php?t=1945811](http://ubuntuforums.org/showthread.php?t=1945811)

---

