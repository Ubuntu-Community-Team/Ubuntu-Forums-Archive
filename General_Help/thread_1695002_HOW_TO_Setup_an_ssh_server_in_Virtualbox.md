---
title: "HOW TO: Setup an ssh server in Virtualbox"
date: 2011-02-25
forum: General Help
---

### Post by JohnElway on 2011-02-25
It took me awhile to do this cause I'm kind of a noob, so I thought I'd post this in case anyone else is interested in attempting this.

Basically I wanted to setup an ssh server on my computer that I, along with some other people I know, could access from outside my home network. I didn't want to give others access to my computer (even if that access was limited), so I wanted to setup the server within a Virtualbox virtual machine. 

**STEP 1: Create the virtual machine**

Create a vm with the distro of your choice. I won't explain how to do that here since there are TONS of guides online about how to do this. Once the vm has been created, be sure to install an ssh server:

```
sudo apt-get install openssh-server
```[B]

STEP 2: Configure the host to send info to the vm

[/B]I found an article that explains why you have to do this and how to do it:
[http://mydebian.blogdns.org/?p=148](http://mydebian.blogdns.org/?p=148)

I can summarize the article by saying that the vm is hidden from other network computers by the host computer. Therefore, you have to configure the host to send information received on a particular port (any port you choose greater than or equal to 1024 as explained in the above link) to port 22 of the vm (port 22 is the default port for ssh). Use these commands to do that:

```
VBoxManage setextradata <guestname> "VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort" 2222
VBoxManage setextradata <guestname> "VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort" 22
VBoxManage setextradata <guestname> "VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/Protocol" TCP
```NOTE: When I followed these directions I got an error saying that the MAC address of the vm could not be retrieved. I don't fully understand the error, but I was able to fix it by going into the vm's Settings, selecting Network, clicking on Advanced, and changing the Adaptor Type from 'intel pro/1000' to 'pcnet'.

**STEP 3: Configure the router**

I can't give out specific details about this since each router has its own interface, but you need to do two things: setup a static local ip address for your host computer and enable port forwarding for the port you chose in the above step. 

The static ip ensures that your router assigns the same local ip address to your computer every time it connects to the internet. Port forwarding tells your router that, whenever it receives data on a particular port, to send that data to a particular ip address (i.e. the static ip address you've setup for your host computer).


You should now be able to connect to your vm by ssh-ing your external ip address (can find it at [www.whatismyip.com]("http://www.whatismyip.com")) on the port that you've previously chosen. The inconvenience of this is that your external ip is probably dynamic, meaning that you will have to look it up every time you want to ssh into your vm. You can get around this by using some kind of dynamic DNS service, although I haven't tried this yet and can't comment on it.

---

### Post by Jonher937 on 2011-02-25
ty :D

---

