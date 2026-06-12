---
title: "Connecting to wireless internet."
date: 2011-09-06
forum: General Help
---

### Post by DrobbinsMpharm on 2011-09-06
Hello.
I have just installed Lunix Ubunto version 11.04 after accidentally wiping my entire hardrive of my Dell Inspiron. ( was running windows vista as my operating system)
I had to boot it using the Lunix CD and have successfully installed in into my laptop.
However, I cannot connect to my wireless router! this is so frustrating.
There is apparently NO wireless networks detected so I cannot connect.
I was wondering if I have deleted any wireless capabilities which were on my hardrive prior to wiping it. Is that even possible? if so, how do i resolve it?
What do I do!?
regards. Dan Robbins

---

### Post by pqwoerituytrueiwoq on 2011-09-06
post the output of lspci
type lspci in a terminal and press enter
is wireless enable under your network icon (right click)?

---

### Post by DrobbinsMpharm on 2011-09-06
I cannot post the output as I have no internet on my Dell and am sunning vista on this laptop so Lumix files cannot be compied onto my windows PC.
I have no network icon on the right click? and lspci on terminal shows nothing of wireless conectivity?
dan

---

### Post by pqwoerituytrueiwoq on 2011-09-06
yuo can save the output of the command to a text file on vista from a live cd
yuo can also save it to flash drive
the output will tell us what hardware is in the computer this included the wireless card you may need a driver for it
for example mine has this in it
```
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```
the thing you click on to see the no networks available is the network applet

---

### Post by DrobbinsMpharm on 2011-09-06
Ok, i am now using my dell, running internet via ethernet cable.
this is my output to your terminal command. I hope this helps.
dan@dan-Inspiron-1545:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
dan@dan-Inspiron-1545:~$ 

Regards. Dan Robbins

---

### Post by pqwoerituytrueiwoq on 2011-09-06
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
that has what you need to do to get it working
the last line of the output had the wireless

-----------

basically since you have a ethernet connection to you can do this in a terminal:
```
sudo apt-get update;sudo apt-get install bcmwl-kernel-source;sudo reboot
```if it does not work reinstall bcmwl-kernel-source via synaptic

---

### Post by DrobbinsMpharm on 2011-09-06
Thank you! as you know, i am a complete newbie to Lumix operating system. Following that link you gave me, on step 2, it says to go to the System via,
 "Under the desktop menu **System > Administration > Hardware/Additional Drivers**,"
I cannot find "System". I have searched "system" "administration" and "hardware/additional drivers" using the search tool at the top left of the desktop and still cannot find it.
I know this is trivial, but i've never used Lumix, :)

---

### Post by DrobbinsMpharm on 2011-09-06
Ok, following my previous reply, my desktop has changed from having a vertical toolbar on the left hand side, to having a rather bare screen with, "applications", "places" and "system" on the top left. On pressing system > administration etc, I receive no response? Any thoughts on what is going on?

---

### Post by pqwoerituytrueiwoq on 2011-09-06
just run the code i posted above in a terminal type password even though you cant see it
i am still running 10.04 so i don't have to deal with the thing called unity that you have

searching for hardware driver should do it in unity

---

### Post by DrobbinsMpharm on 2011-09-06
I have tried that - Still no wireless networks found. :(

---

### Post by DrobbinsMpharm on 2011-09-06
Do you think you could solve this via remote access by any chance? :confused:

---

### Post by pqwoerituytrueiwoq on 2011-09-06
open synaptic
search for bcmwl-kernel-source
right click it and click mark for reinstallation then click apply
edit 
possibly do yuo have port forwarding setup for the vnc clients on ubuntu or have teamviewer installed?

---

### Post by ubun2geek on 2011-09-06
Click System > Administration > Additional Drivers
You probably need to install a driver Hope this helps! :)

---

### Post by DrobbinsMpharm on 2011-09-06
I am yet to connect to the wireless internet.
I have done this as told. [I]"open synaptic
search for bcmwl-kernel-source
right click it and click mark for reinstallation then click apply"[/I]
I do not know how to check this. *"possibly do yuo have port forwarding setup for the vnc clients on ubuntu or have teamviewer installed?"*

I have also clicked on system > Administration > Additional Drivers
to be shown this message.
"broadcom STA wireless driver (this driver is not activated)
followed by: "Broadcom STA wireless driver, this package contains Broadcom 802.11 linux STA wireless driverfor use with broadcom's BCM4311-,BCM4312-,BCM4313..... and so on.
When i try to active it, I am given this message; "SORRY, INSTALLATION OF DRIVER FAILED. PLEASE HAVE A LOOK AT THE LOG FILE FOR DETAILS:/VAR/LOG/JOCKEY.LOG

Thank you for your patience.
Dan

---

### Post by pqwoerituytrueiwoq on 2011-09-06
```
cat /var/log/jockey.log
```post that here
you can always try 10.04 the current lts release if all else fails
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by DrobbinsMpharm on 2011-09-07
Would just like to let you know, I solved the problem, Thank you very much for your help!):P

---

