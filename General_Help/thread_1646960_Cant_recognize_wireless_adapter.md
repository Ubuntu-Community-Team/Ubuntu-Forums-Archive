---
title: "Cant recognize wireless adapter"
date: 2010-12-16
forum: General Help
---

### Post by loykianos on 2010-12-16
So, i know there are probably tens of threads like this, but i m really bugged about this. Here is my problem. I installed ubuntu 10.04 LTS on my netbook a few months ago. So, obviously, i had to go through all those wireless troubleshooting guides. Well, it didnt quite get me anywhere. I cant seem to find my wireless adapter. I 've tried lspci, lsusb, but nothing comes up. So i cant even beggin to fix the problem. I 'd appreciate it if someone could help. Maybe point out which one my wireless adapter is? This is the -lspci output.

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

And here is the lsusb output.

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Is it possible that ubuntu cant even recognize my adapter? 'Cause my wireless works fine on Windows. And sorry again if my question is stupid, but its urgent. Thanks in advance.

---

### Post by mmsmc on 2010-12-16
its probably your drivers try this
If you no longer want to install that broadcom drivers, you can get rid of that error by manually editing some files.

Your apt cache has got corrupted. Time for some clean up. Follow with  caution, keep a close eye and your mind on what you are doing and double  check before deleting any files/text as advised.

Type
 	Code:
 	gksu nautilus /var/lib/dpkg/info 
Find firmware-b43-installer, any files relating to it and rename  them, delete them or move them to some other location whatever you  prefer.

Now make a backup of your dpkg status file as you are going to edit it and might need to revert back to the original in case.

 	Code:
 	sudo cp /var/lib/dpgk/status /var/lib/dpkg/status.bak 
Now edit the file

 	Code:
 	gksu gedit /var/lib/dpkg/status 
Search for firmware-b43-installer and delete any lines relating to  it. There might be more than one so go keep on searching until the end  of the file.

Now type

 	Code:
 	sudo apt-get update 
And tell me that the error message is gone. :smile:


[COLOR=Red]**EDIT:**[/COLOR] **You are doing everything as  root, the system might not ask you to double check or even single check  if deleting something. Be cautious or you might mess up your system.**
 		                   		  		  		 		 			 				__________________
follow it step by step

---

### Post by cariboo on 2010-12-16
Can you boot into Windows, and find the make/model of your wireless device?

---

### Post by loykianos on 2010-12-16
> **mmsmc said:**
> its probably your drivers try this
If you no longer want to install that broadcom drivers, you can get rid of that error by manually editing some files.

Your apt cache has got corrupted. Time for some clean up. Follow with  caution, keep a close eye and your mind on what you are doing and double  check before deleting any files/text as advised.

Type
     Code:
     gksu nautilus /var/lib/dpkg/info 
Find firmware-b43-installer, any files relating to it and rename  them, delete them or move them to some other location whatever you  prefer.

Now make a backup of your dpkg status file as you are going to edit it and might need to revert back to the original in case.

     Code:
     sudo cp /var/lib/dpgk/status /var/lib/dpkg/status.bak 
Now edit the file

     Code:
     gksu gedit /var/lib/dpkg/status 
Search for firmware-b43-installer and delete any lines relating to  it. There might be more than one so go keep on searching until the end  of the file.

Now type

     Code:
     sudo apt-get update 
And tell me that the error message is gone. :smile:


[COLOR=Red]**EDIT:**[/COLOR] **You are doing everything as  root, the system might not ask you to double check or even single check  if deleting something. Be cautious or you might mess up your system.**
                                                                                               __________________
follow it step by step
I cant seem to find any files/records with the name firmware or something similar. I mistyped my ubuntu version, if it has anything to do with that. My version is 10.04.

> **cariboo907 said:**
> Can you boot into Windows, and find the make/model of your wireless device?

And no. I dont have windows anymore. Although, i did try to find my wireless device model, but couldnt. It was named Wireless Adapter or something general like that. Cant remember exactly.

---

### Post by mmsmc on 2010-12-16
go to system --> administration--> additional drvers and tell me whats listed

---

### Post by loykianos on 2010-12-16
System -> Administration -> Hardware Drivers

No proprietary drivers are in use on this system.

Nothing is shown below. Just the Help and Close button.

---

### Post by mmsmc on 2010-12-16
it should read sta and broadcom
cariboo907 do you know how to get them?

---

### Post by loykianos on 2010-12-16
Anyways, i 'm really frustrated by this. I 've been trying to solve this problem for months with no luck. I might end up calling the manifacturer. Thanks for your help!

---

### Post by mmsmc on 2010-12-16
dont do that, look around how to install these your missing them(it happens with every dell comp)
Broadcom b43
and sta wireless drivers
also try sudo apt-get update(i thinjk thats the right code)

---

### Post by mmsmc on 2010-12-16
System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close

---

