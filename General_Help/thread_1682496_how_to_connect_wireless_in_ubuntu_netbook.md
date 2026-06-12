---
title: "how to connect wireless in ubuntu netbook"
date: 2011-02-06
forum: General Help
---

### Post by cjprofile on 2011-02-06
i have installed ubuntu 10.10
and cant connect to internet.. 
i have dell mini inspiron 10 cant use wireless...ive tried to follow the steps in google but cant make it.. ubuntu is complicated..

---

### Post by RedSingularity on 2011-02-06
Is the wireless card detecting any networks?

---

### Post by whatthefunk on 2011-02-06
Is your hardware detected by the system?

---

### Post by cjprofile on 2011-02-06
im sorry guys im just a newbie, how can i know that my netbook unbuntu is not detecting my hardware ?? but looks like its not detecting my hardware

---

### Post by some1here on 2011-02-06
The below work for my Inspiron 1018.

[http://art.ubuntuforums.org/showthread.php?p=10397691](http://art.ubuntuforums.org/showthread.php?p=10397691)
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

---

### Post by cjprofile on 2011-02-06
do u have like easier one,,  im lost... too complicated , im too noob for ubuntu
thanks for the help tho

---

### Post by madmarx on 2011-02-06
I suggest a couple quick checks:
(1) Is wifi enabled in the BIOS? It typically is, just in case.
(2) Does your netbook have an on/off switch for wifi? Typically using an Fn key bottom left + a function key. Make sure it is on.
(3) Now in Ubuntu, go to System | Administration | Network tools. The first tab shows a list of detected network hardwares. Does the wifi interface show?
(4) Top right, around where the date shows, there is an icon for network connection & setup. A simple left click should show a menu with available wireless connections. If the hardware in on and the driver is OK.

Check [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks) for further info on your specific laptop compatibility. Dell Mini 10 seems OK out of the box.

I hope that you will actually find network setup really simple when you look in the right places :)

---

### Post by Spyderkid on 2011-02-06
Easier Instructions:

>Is it a wireless USB dongle or a card?
>is its a dongle go to Applications > Accessories > Terminal, then type into   Terminal ***lsusb*** and press enter.
>then post here the output.

---

### Post by RedSingularity on 2011-02-06
Dell mini probably has a built in card.  In that case the command "lspci" will display the card info if the system detects it.

---

### Post by cjprofile on 2011-02-06
> **Spyderkid said:**
> Easier Instructions:

>Is it a wireless USB dongle or a card?
>is its a dongle go to Applications > Accessories > Terminal, then type into   Terminal ***lsusb*** and press enter.
>then post here the output.
 Bus 005 Device 002: ID 192f:0716  Avago Technologies, Pte.
 "       "      "          001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 "      004  "           "       "     "         "       "          "              "       "     "
 "      003  "           "       "     "         "       "          "              "       "     "
 "      002  "           "       "     "         "       "          "              "       "     "
 "      001  "          004: ID 0bda: 0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
 "      001  "          003: ID 174f:1403 syntek Integrated webcam
 "      001  "          002: ID Ia40: 0101 TERMINUS TECHNOLOGY INC. USB -2.0 4-Port HUB 
 "      001  "          001: ID 1d6b: 0002 Linux Foundation 2.0 root hub
cj@cj-Inspiron-1011:-s

---

### Post by cjprofile on 2011-02-06
> **madmarx said:**
> I suggest a couple quick checks:
(1) Is wifi enabled in the BIOS? It typically is, just in case.
(2) Does your netbook have an on/off switch for wifi? Typically using an Fn key bottom left + a function key. Make sure it is on.
(3) Now in Ubuntu, go to System | Administration | Network tools. The first tab shows a list of detected network hardwares. Does the wifi interface show?
(4) Top right, around where the date shows, there is an icon for network connection & setup. A simple left click should show a menu with available wireless connections. If the hardware in on and the driver is OK.

Check [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks) for further info on your specific laptop compatibility. Dell Mini 10 seems OK out of the box.

I hope that you will actually find network setup really simple when you look in the right places :)
i tried when i left click the icon it hows enable networking (check) enable wireless(check) enable notifications(check)

when i right click that icon it shows me 
wired network (disconnected)
Wireless Networks (device not ready firmware missing)

---

### Post by cjprofile on 2011-02-06
> **RedSingularity said:**
> Dell mini probably has a built in card.  In that case the command "lspci" will display the card info if the system detects it.
   	 	 	 	p { margin-bottom: 0.21cm; }  cj@cj-Inspiron-1011:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)  
 00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)  
 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)  
 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)  
 cj@cj-Inspiron-1011:~$

---

### Post by marshag63 on 2011-02-06
Looks like it is a BCM4312.

Grab an ethernet cable and try this.

[http://jetpackweb.com/blog/2010/04/30/ubuntu-10-4-lucid-lynx-and-broadcom-bcm4312/](http://jetpackweb.com/blog/2010/04/30/ubuntu-10-4-lucid-lynx-and-broadcom-bcm4312/)

Hope this helps.

MarshaG63

---

### Post by cjprofile on 2011-02-07
sudocj@cj-Inspiron-1011:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for cj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 250 not upgraded.
1 not fully installed or removed.
Need to get 0B/896kB of archives.
After this operation, 2,597kB of additional disk space will be used.
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 118708 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-22-generic/updates/dkms/

depmod.........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
cj@cj-Inspiron-1011:~$ 


seems like didnt work or ive done it wrong??

---

### Post by RedSingularity on 2011-02-07
Try installing the following:

sudo apt-get install b43-fwcutter

Then do:

sudo apt-get install bcmwl-kernel-source

---

### Post by cjprofile on 2011-02-08
do u know how to uninstall ubuntu 10.10 i want to uninstall it.. seems like  my dell mini inspiron 10 doesnt have much of memory to handle 2 O.S

---

### Post by RedSingularity on 2011-02-08
You cant "uninstall" it.  You can format over it though to make free space.  You will need to boot from a USB drive and choose to "try ubuntu".  Then use a program called "gparted" to format the space you want.  It will need to be formated into something windows readable like ntfs or fat 32.  

NOTE:  Dont attempt unless you are confident that you know what your doing.  This could result in data loss or a corrupted system.

---

### Post by Spyderkid on 2011-02-19
just install the new OS and it will give you the option to remove the old one.

Kubuntu or Lubuntu would be good.

or of course you could go for the expensive route of XP or 2000

---

### Post by sugarland2k on 2011-02-22
I have a Dell Mini 9 and I almost always have to plug it into my wired network to add and install the restricted driver for the built-in Broadcom wireless in the Mini 9.  

Check System/Additional Drivers and activate the Broadcom STA wireless driver or as needed.  You will need to enter your SUDO password...

---

