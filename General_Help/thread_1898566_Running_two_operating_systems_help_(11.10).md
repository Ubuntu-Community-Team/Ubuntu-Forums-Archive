---
title: "Running two operating systems help (11.10)"
date: 2011-12-21
forum: General Help
---

### Post by H_J_C on 2011-12-21
inspiron 1545
intel duo core cpu
RAM 3G
HDD 500G

I cant connect to the internet with ubunutu 11.10 but i still love the operating system for other stuff, is there a way i can run vista for internet browsing and ubunutu 11.10 for everything else on the same hard drive? 

thanks

---

### Post by TeoBigusGeekus on 2011-12-21
Is it a wired or wireless connection?

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> Is it a wired or wireless connection?

wireless connection

---

### Post by TeoBigusGeekus on 2011-12-21
Let's try to fix your internet connection in ubuntu and then we can talk about vista, shall we?

Have you looked in "Additional Drivers" to see if there's a driver for your wireless card?

---

### Post by H_J_C on 2011-12-21
[img]http://i.imgur.com/bjGs9.png

im a complete noob so i dont know what im looking at so i'll just post screen shots while my internet is still working.

---

### Post by TeoBigusGeekus on 2011-12-21
> **H_J_C said:**
> 
im a complete noob so i dont know what im looking at so i'll just post screen shots while my internet is still working.

Wait! So your internet does work, or not?

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> Wait! So your internet does work, or not?

sometimes i connect when i turn on my computer and it will work for a few days and sometimes it will not connect and just say obtaining ip address for ages. Today its working for some reason but thats why i wanted to run vista with ubuntu so i would have internet all the time.

---

### Post by TeoBigusGeekus on 2011-12-21
I see.
Try this: install wicd from the software centre. It's a network manager, alternative to the default ubuntu one; it's always been better with wireless connections.

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> I see.
Try this: install wicd from the software centre. It's a network manager, alternative to the default ubuntu one; it's always been better with wireless connections.

already tryed that im running it at the moment, i think iv tryed everything tbh which is why i wanted to run vista with ubuntu as a last resort.

---

### Post by TeoBigusGeekus on 2011-12-21
What's your wireless card?
Post us the output of 
```
lshw -C network
```

It is possible to run vista alongside ubuntu, either as a dual boot or as a virtual machine, but it would be simpler and easier if we could find a solution for you from inside ubuntu.

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> What's your wireless card?
Post us the output of 
```
lshw -C network
```

It is possible to run vista alongside ubuntu, either as a dual boot or as a virtual machine, but it would be simpler and easier if we could find a solution for you from inside ubuntu.

-Inspiron-1545:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 70:1a:04:36:12:08
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.66 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:64:b1:76
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by TeoBigusGeekus on 2011-12-21
BCM4312 it is then.
See the 4rth post in [this]("http://ubuntuforums.org/showthread.php?t=1896336") thread.
To do this of course you have to have a wired connection - do you?

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> BCM4312 it is then.
See the 4rth post in [this]("http://ubuntuforums.org/showthread.php?t=1896336") thread.
To do this of course you have to have a wired connection - do you?

nope :S soz 

i wouldnt even know how to set up a wired connection anyway lol

---

### Post by TeoBigusGeekus on 2011-12-21
I mean a cable going straight from your router to your ethernet card.

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> I mean a cable going straight from your router to your ethernet card.

no i dont have that :S

---

### Post by TeoBigusGeekus on 2011-12-21
Ok, if we try to uninstall Broadcom's driver and install the native linux one, something could go wrong; do you have a friend/relative to whom you can go to get internet access and fix things?

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> Ok, if we try to uninstall Broadcom's driver and install the native linux one, something could go wrong; do you have a friend/relative to whom you can go to get internet access and fix things?

Yeh i have a family computer i could use if things go wrong, but wouldnt it be easier to just run vista and ubuntu at the same time?

I feel like iv spent so much time trying to fix the wireless when i installed ubuntu that i just want a easy life now lol

---

### Post by TeoBigusGeekus on 2011-12-21
You could be one step from fixing your problem.
Ok:
Open a terminal and give
```
cd ~/Desktop
```
to go to your Desktop. Then
```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
```
to download the broadcom firmware. Then go again to Additional Drivers and remove the proprietary Broadcom driver. After that
```
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
sudo modprobe -rfv wl
cd b43/
make clean
make
sudo make uninstall
sudo modprobe -v b43
```
Reboot, cross your fingers and report back.

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> You could be one step from fixing your problem.
Ok:
Open a terminal and give
```
cd ~/Desktop
```
to go to your Desktop. Then
```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
```
to download the broadcom firmware. Then go again to Additional Drivers and remove the proprietary Broadcom driver. After that
```
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
sudo modprobe -rfv wl
cd b43/
make clean
make
sudo make uninstall
sudo modprobe -v b43
```
Reboot, cross your fingers and report back.

i think iv already done this? is there anyway we can check cause i feel like i done this following some of the stickies in the web connection sub-forum

---

### Post by TeoBigusGeekus on 2011-12-21
I don't think you've done this before, cause you're using Broadcom's driver.
These steps will install the native linux driver, which, reportedly works better.

---

### Post by H_J_C on 2011-12-21
> **TeoBigusGeekus said:**
> I don't think you've done this before, cause you're using Broadcom's driver.
These steps will install the native linux driver, which, reportedly works better.

ok soz, i remember installing synaptic package manager and downloading something to do with firmware when i was following one of the stickies on one of the sub-forums.

anyway do i just put into the terminal exactly as you wrote?

---

### Post by TeoBigusGeekus on 2011-12-21
Yes.

---

