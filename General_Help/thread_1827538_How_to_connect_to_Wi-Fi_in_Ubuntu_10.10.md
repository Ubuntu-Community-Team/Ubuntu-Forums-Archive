---
title: "How to connect to Wi-Fi in Ubuntu 10.10?"
date: 2011-08-18
forum: General Help
---

### Post by community on 2011-08-18
I have Ubuntu 10.10 installed in my laptop along with Win 7.I need to connect to a WiFi in Ubuntu.Please tell me the procedure for the same...

---

### Post by gandaran on 2011-08-18
> **community said:**
> I have Ubuntu 10.10 installed in my laptop along with Win 7.I need to connect to a WiFi in Ubuntu.Please tell me the procedure for the same...
click on the panel network icon, if it is detecting networks just select one to connect, if it's not detecting anything you need to install wireless drivers.
using wired internet check additional drivers if any exist there to activate.
to find out what drivers are needed you have to know the wireless chipset brand, to ckeck brand type in terminal
```
lspci
```
for internal devices
```
lsusb
```
for usb devices
paste the output here

---

### Post by allwimb on 2011-08-18
please paste the result of the commande sudo iwconfig we will tell you if your card is ready to be used or not.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by Actonix on 2011-08-18
> **community said:**
> I have Ubuntu 10.10 installed in my laptop along with Win 7.I need to connect to a WiFi in Ubuntu.Please tell me the procedure for the same...

**Pre-requisites**
  1. Properly installed driver for your wifi interface
2. The ESSID of your router should be broadcast and not hidden at least for the install
3.  Your wireless card&#8217;s Interface Name -  ie wlan0, ath0, etc

... I am assuming you are familiar with your Router setup. 
 
To check that you satisfy the prerequisites, open up a terminal window and type "sudo lshw  -C network"  ... you will need to run this as a sudoer (Administrative  User) and will be prompted to input your password - the command provides  a detailed list of all network hardware found. Your wireless card will  probably be identified with the generic name "wlan0" and will show a  driver bound to the device (driver=...), if unclaimed you need to install the driver - in X go to System > Administration > Additional drivers to check and install - you might need to use a wired Ethernet connection but there might be alternatives.

If the above command showed a driver bound to the device then  run the command  "sudo lspci -v" to verify the driver is loaded. - verify  against the driver name listed in the output of lshw.

The "sudo iwconfig" command prints information about the wireless  interface and enables you to configure the network interface from the  command line - alternatively load up Network Tools or Network  Connections for a GUI interface and seek out the Wireless tab under  connections.

Run the command "sudo iwlist scan"  to scan for a router. If this succeeds in identifying access point then  your card is working properly, note however that not all cards support  scanning.

The command "ifconfig" can be used to verify your assigned IP, Sub-Net and Gateway among other things

At the command-line run "ping google.com -c 4" and if you get a response  you've done it,
... if not post back here for further assistance providing the output from the above commands.

---

### Post by community on 2011-08-18
Thank you.But how could I install the drivers if they are not currently installed on my system??

---

### Post by Idefix82 on 2011-08-18
First things first. Open the terminal (Applications->Accessories->Terminal), type in
```

lshw -C network

```
and paste the output here. We will take it from there.

---

### Post by community on 2011-08-18
Here is the output on running the command lshw -C network 
 
 *-network UNCLAIMED            
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:04:00.0"]pci@0000:04:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: [EMAIL="pci@0000:05:00.0"]pci@0000:05:00.0[/EMAIL]
       logical name: eth0
       version: c1
       serial: 14:fe:b5:9b:1f:7e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:f0200000-f023ffff ioport:3000(size=128)

---

### Post by gandaran on 2011-08-18
> *-network UNCLAIMED 
description: Network controller
product: BCM4313 802.11b/g LP-PHY
vendor: Broadcom Corporation
did you check additional drivers for broadcom drivers? they could be there just needing activation, (must be connected with wired internet)
follow this thread to find correct broadcom driver
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
you still need to connect to wired internet to install them from software package manager.

---

### Post by Actonix on 2011-08-18
> **gandaran said:**
> did you check additional drivers for broadcom drivers? they could be there just needing activation, (must be connected with wired internet)
follow this thread to find correct broadcom driver
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
you still need to connect to wired internet to install them from software package manager.

As Gandaran advices ^ +

...just  to summarise and keep you from having to hop about,

First off, hopefully your Ethernet connection is setup and configured as I see it does have drivers against it - so connect your ethernet cable and hook up to the internet

...  that done, open Synaptic, click on settings, then repositories and put a check  by multiverse, click on reload and with that done close Synaptic

... now in terminal run "sudo apt-get update && sudo apt-get upgrade"  [FONT=monospace]- [/FONT]the upgrade can take a while so be patient,
... when that is done run "sudo apt-get install firmware-b43-installer"[FONT=monospace]

[/FONT]... now disconnect your wired connection, restart your computer and verify as per instructed earlier  or just go ahead and try see if you can browse ok.

---

