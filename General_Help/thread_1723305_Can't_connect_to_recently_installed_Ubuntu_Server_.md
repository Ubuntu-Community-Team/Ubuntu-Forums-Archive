---
title: "Can't connect to recently installed Ubuntu Server (10.04) via SSH"
date: 2011-04-06
forum: General Help
---

### Post by bfin on 2011-04-06
**Issue:**
Can't connect to a recently installed Ubuntu Server (10.04) via SSH.

**Goal:**
Run Ubuntu Server on an HP Mediasmart Server EX485.

**Background:**
The Mediasmart Server line is headless (with no hookup ports) and comes with WHS installed. I'm trying to replace WHS with Ubuntu Server. I only have laptop computers, so I took a spare 3.5" hard drive and connected it to my laptop via USB-SATA cable. My intent was to install Ubuntu Server on the external drive, then replace my system drive in the Mediasmart Server with the external drive.

I booted the laptop computer to an Ubuntu Server install DVD and installed to the external drive. During the install, I elected to install the OpenSSH Server and Samba File Server.

I then ran the following commands:
```
sudo apt-get update
sudo aptitude safe-upgrade
```

I then restarted the system with the command:
```
sudo reboot -h now
```

After the reboot, I logged in with the account username and password I established during the install. I currently cannot connect to the server from my other laptop, and I cannot connect to my laptop from the server.

Tried the commands:
```
sudo aptitude install openssh-server
sudo update-rc.d ssh defaults
```

My /etc/network/interfaces file is set to:
auto eth0
iface eth0 inet dhcp

The laptop I have connected to the external drive is a Dell XPS M1330 running Ubuntu Netbook Edition 10.10. The laptop I'm using to test the SSH connection is a Macbook Pro running Mac OS X 10.6.7. My router is an Apple Airport Extreme Base Station.

Ideas???

Thanks.

---

### Post by bfin on 2011-04-07
When I try to connect to the server with SSH using
```
ssh *username*@*hostname*
```
or
```
ssh *username*@*ipaddress*
```

I get the response:
```
ssh: connect to host server port 22: Operation timed out
```

Seems strange to me that the install could get updates from the internet, and the SSH server is running, but I can't connect to it with SSH...

---

### Post by seawolf167 on 2011-04-07
Do you have port 22 forwarded from your router to your computer?

---

### Post by kamzhang on 2011-04-07
Port has been changed?

---

### Post by Fire_Chief on 2011-04-07
Have you started the OpenSSH server? ```
/etc/init.d/sshd start
/etc/init.d/sshd status
```

Do you have a firewall running on the Ubuntu system?
Can you ping the IP address you are trying to connect to and can the Ubuntu system ping your workstation?

Cheers!

---

### Post by CharlesA on 2011-04-07
> **seawolf167 said:**
> Do you have port 22 forwarded from your router to your computer?
That shouldn't have anything to do with it, unless you are accessing the machine from outside your local network.

By default Ubuntu server doesn't have openssh-server installed, unless you select it during install or install it after.

See if you can ping it, otherwise, try running a scan with nmap against the box to see which ports are open.

---

### Post by seawolf167 on 2011-04-07
I thought he was attempting to access his computer from outside his LAN network - though I was wrong I missed the part about simply testing it.

The other suggestions are good though - check to ensure ssh is running & that you still are using the default port 22 in */etc/ssh/sshd_config*

---

### Post by bfin on 2011-04-07
> **seawolf167 said:**
> Do you have port 22 forwarded from your router to your computer?

I have not configured any port forwarding from my router.

---

### Post by seawolf167 on 2011-04-07
> **bfin said:**
> I have not configured any port forwarding from my router.

I got called out on this earlier because I didn't fully read your post - if you are connecting from within your LAN you won't need to forward port 22 to your computer. You'll only need to do this once you get it working and want to access your box from outside your LAN

---

### Post by bfin on 2011-04-07
> **Fire_Chief said:**
> Have you started the OpenSSH server? ```
/etc/init.d/sshd start
/etc/init.d/sshd status
```

When I ran those 2 commands I received
```
-bash: /etc/init.d/sshd: No such file or directory
```

> Do you have a firewall running on the Ubuntu system?
No firewall on the Ubuntu system, only the initial installation.

> Can you ping the IP address you are trying to connect to and can the Ubuntu system ping your workstation?
From the Ubuntu Server (hostname="server"):
**This identified the problem for me! The server could ping itself and my laptop could ping the server, but my laptop couldn't ping itself. Realized that the laptop was running a firewall and wouldn't allow the SSH connection with the server.**

---

### Post by bfin on 2011-04-07
Thanks to everyone for helping me with this problem! I'm obviously new to all of this. I appreciate your time and effort.

---

### Post by seawolf167 on 2011-04-07
> **bfin said:**
> When I ran those 2 commands I received
```
-bash: /etc/init.d/sshd: No such file or directory
```
No firewall on the Ubuntu system, only the initial installation

Just FYI, the correct commands are:

```
sudo service ssh status
sudo service ssh start|restart|stop
```

---

### Post by bfin on 2011-04-07
Thanks. That makes more sense. Response was:
```
ssh start/running, process 1024
```

---

