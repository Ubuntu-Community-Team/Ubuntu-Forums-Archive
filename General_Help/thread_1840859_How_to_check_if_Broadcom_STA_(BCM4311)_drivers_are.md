---
title: "How to check if Broadcom STA (BCM4311) drivers are installed?"
date: 2011-09-08
forum: General Help
---

### Post by amitsaini on 2011-09-08
Please help...
I just want to check if my  Broadcom STA (BCM4311) are installed. how to check from the terminal?
In the Ubuntu software package it it displaying but how to check from the terminal which command is to be used?
Waiting in anticipation:confused:...

---

### Post by Enigmapond on 2011-09-08
Not knowing what distro you are running, navigate to System/Administration/Additional Drivers (or Hardware Drivers) and it will tell you if activated.

---

### Post by amitsaini on 2011-09-08
I am using a Compaq Presario C500.

---

### Post by amitsaini on 2011-09-08
I have just installed Ubuntu 11.04

---

### Post by amitsaini on 2011-09-08
Thanks a ton Enigmapond. I just confirmed the same. But is there a way to know if these drivers are active thru the terminal?

---

### Post by Enigmapond on 2011-09-08
Sure...one way is:

```
sudo lshw -C network
```

---

### Post by amitsaini on 2011-09-08
I did as you told and got the following result:

aks@aks-Presario-C500-RU914PA-ACJ:~$ sudo lshw -C network
[sudo] password for aks: 
  *-network DISABLED      
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:0b:c3:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:50400000-50403fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:a4:43:99
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
aks@aks-Presario-C500-RU914PA-ACJ:~$ ^C
aks@aks-Presario-C500-RU914PA-ACJ:~$ 



How to see the status of activation of wireless drivers and it also shows that network is disabled?
Please help.

---

### Post by ajgreeny on 2011-09-08
Try ```
modprobe -l | grep -i bcm
```which will tell you if it is installed, and if it is the 4311 or another that is current.

---

### Post by TBABill on 2011-09-08
Probably isn't activated if you haven't taken the steps to actually install the driver and firmware. That won't happen automatically since the firmware is proprietary. 
 
If you just want to get it going you'll need the b43 driver for Natty. For some reason the STA won't work in 11.04 but works fine in previous versions.
 
Easy way is to ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by amitsaini on 2011-09-08
Can you plz specify again? Is it

modprobe -l  and  grep -i bcm seperately?
Are these two different commands????
(Sorry to bug u but i am new to ubuntu)

---

### Post by amitsaini on 2011-09-08
I have already downloaded and installed drivers for broadcom 4311. Do i still need to install b43 driver for Natty??

---

### Post by TBABill on 2011-09-08
What exactly did you download and from where did you download it?

---

### Post by 3rdalbum on 2011-09-08
Sounds like a silly answer, but it isn't. The best way of checking if your wireless driver is installed is to see if Network Manager is detecting any networks, and if it isn't, then seeing if it's reporting "Firmware Missing" next to your card's name in the Network Manager menu.

---

### Post by TBABill on 2011-09-08
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
 
Guidance in that link for installing. If you downloaded from Broadcom directly then you may be able to get the STA driver to work, but I have not seen posts of people with your card stating that's the case. To check, you can simply open a terminal and ```
sudo modprobe wl
``` After waiting up to a minute you should then see networks when you click network manager IF you installed the driver properly and it works properly with 11.04. If not, the b43 driver is probably your best bet using the instructions I posted previously and you can confirm their validity at the link above.

---

### Post by MARP1961 on 2011-09-08
Natty and 'Additional Drivers' seems to unhelpfully nag you to install the STA driver which does not seem to work with this wireless card. To make matters worse, it does not give you the B43 option at all (Lucid did). This is all further complicated by causing B43 to be blacklisted if you attempt to install it via Synaptic!

I suceeded in the end by doing a fresh install of Natty, ignoring Additional Drivers and installing B43 fwcutter from Synaptic.

This might be useful to read:[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04")

---

### Post by wildmanne39 on 2011-09-08
Hi, the sta driver for that card does not work in 11.04 you need to get rid of it this should do it
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source bcmwl-modaliases
```
Then 
```
sudo apt-get --purge autoremove
```

Then run this command please
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
disconnect your wired connection and restart your computer.

If it still does not connect we probably need to fix a blacklist issue so post the results of these commands here please:
```
cat /etc/modprobe.d/blacklist.conf
```
```
lsmod
```
Thank you

---

