---
title: "No IP Address until local login"
date: 2009-09-22
forum: General Help
---

### Post by leveneficus on 2009-09-22
Hi there,
 
I am using Ubuntu 9.04 with 2.6.28-13-generic Kernel. I was remotely updating my system over SSH connection the other day and had to reboot the system. Upon reboot the system did not set the IP address until I logged in locally. 
 
I am using static IP address and configured it via GUI. How can I make Ubuntu use the static IP address without requiring me to logon locally?
 
Thanks for your help,
-Ven

---

### Post by leveneficus on 2009-09-22
My  etc/network/interfaces file only contains this:
 
auto lo
iface lo inet loopback

 
I guess this is part of the problem, So the network manager is somehow using a different configuration file to set the static IP?

---

### Post by dankdave on 2009-09-22
what kind of modem are you using?  i had to tell my router to set a static ip address for my server.

---

### Post by unutbu on 2009-09-22
Edit /etc/network/interfaces by adding something like
```

iface eth0 inet static
address 192.168.1.81
netmask 255.255.255.0
gateway 192.168.1.1
```

Change "eth0" and the numbers as appropriate for your situation.

---

### Post by leveneficus on 2009-09-22
So, I have followed the instructions given at [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)
and configured my interfaces file, restarted the network, no problem. Ifconfig showed right configuration. Pinged some internet sites, works great. 
 
but then, I rebooted the system and again it does not set the static IP address until I login to ubuntu locally. What gives?

---

### Post by unutbu on 2009-09-22
Please post
```
ls -l /etc/rc2.d | grep -i network
```

---

### Post by leveneficus on 2009-09-22
> **unutbu said:**
> Please post
```
ls -l /etc/rc2.d | grep -i network
```
 
Here it is:
lrwxrwxrwx 1 root root  24 2009-04-30 17:56 S50NetworkManager -> ../init.d/NetworkManager

---

### Post by Iowan on 2009-09-22
> **unutbu said:**
> ```

iface eth0 inet static
address 192.168.1.81
netmask 255.255.255.0
gateway 192.168.1.1
```Might I suggest adding the "auto eth0" line?

---

### Post by leveneficus on 2009-09-22
> **Iowan said:**
> Might I suggest adding the "auto eth0" line?
 
You sure might! :) That did the trick :) 
 
Thank you very much,
-Ven

---

### Post by dcstar on 2009-09-23
> **leveneficus said:**
> Hi there,
 
I am using Ubuntu 9.04 with 2.6.28-13-generic Kernel. I was remotely updating my system over SSH connection the other day and had to reboot the system. Upon reboot the system did not set the IP address until I logged in locally. 
 
I am using static IP address and configured it via GUI. How can I make Ubuntu use the static IP address without requiring me to logon locally?
 
Thanks for your help,
-Ven

Install the **gnome-network-admin** package and remove the **network-manager** package.

Network Manager is a right PITA that only configures your networking via your successful Gnome login session, so until you do that your machine has no networking!

The (old) gnome-network-admin package is a GUI into the /etc/network/interfaces setup so your system has networking going after boot up.

---

