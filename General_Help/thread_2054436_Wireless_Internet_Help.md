---
title: "Wireless Internet Help"
date: 2012-09-07
forum: General Help
---

### Post by strawbell on 2012-09-07
Hi hope someone can help I am trying to make my PC wireless & I have no idea how. I'm with virgin but since being given this computer I have had to connect via a cable. I've bought a dongle but that doesn't seem to install onto ubuntu (10.10) does anyone no how. 

I've also got no password so can't do upgrades etc. Thanks

---

### Post by CrusaderAD on 2012-09-07
You can get a wireless usb adapter pretty cheap now, like 10 bucks. Try one of those. Belkin usually works well out of the box.

---

### Post by strawbell on 2012-09-07
Hi thats what I have just bought but it won't install on ubuntu?? Thanks

---

### Post by steeldriver on 2012-09-07
Hi can we get some details about the dongle please (make / model)?

Also if you open up a terminal (with the dongle plugged in  - I am assuming it's USB?) and type

```
lsusb
```and if possible

```
lshw -C network
```(it will complain that you should run as root - just ignore that) and post the results here that will help us

---

### Post by CrusaderAD on 2012-09-07
10.10 is also pretty old, and I'm sure you're running an old kernel. You might want to format it and upgrade if possible. Start fresh with sudo capabilities. It'll make your life easier in the long run.

---

### Post by strawbell on 2012-09-07
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:1d04 Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tristan@tristan-desktop:~$ 

this is what I get if i type in lsusb

---

### Post by strawbell on 2012-09-07
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:50:8d:d5:fa:1c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.2 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:18 ioport:a000(size=256) memory:fa005000-fa0050ff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 48:02:2a:1a:c2:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
tristan@tristan-desktop:~$ 
tristan@tristan-desktop:~$ 

This is the reply to the other one. Thanks

I can't upgrade as it asks for a password which i don't have. Thanks

---

### Post by steeldriver on 2012-09-07
Unfortunately I think you will need 'sudo' permissions to fix that because you will likely need to build and install a new driver from source

[http://ubuntuforums.org/showthread.php?t=1397309](http://ubuntuforums.org/showthread.php?t=1397309)

Why don't you have a password? does the machine belong to you? if so you can do a password reset from the recovery console

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

**EDIT: didn't see your lshw output before I posted** : since it says 'DISABLED' rather than 'UNCLAIMED' it may actually have a working driver, but just need unblocking - try

```
rfkill list all
```

---

