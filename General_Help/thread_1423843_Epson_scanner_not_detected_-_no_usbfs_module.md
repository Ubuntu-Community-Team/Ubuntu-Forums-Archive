---
title: "Epson scanner not detected - no usbfs module"
date: 2010-03-07
forum: General Help
---

### Post by ndres on 2010-03-07
Have an Epson Expression 1640 XL A3 scanner (usb & network interface card). Bus=0002 Device=004 its usb ID is 0x04b8 0x0109

I have never been able to connect the scanner using the network - if anybody can advise, I would be very grateful. Quite happy to use this if usb is going to be a problem

The scanner has worked very well through the usb and wask working well with 9.04(32bit).
I have bought a new machine and did a fresh install of 9.10 (64bit) and the scanner is not detected.

xsane detects my webcams (vl4:/dev/video*) but no scanner
Have run sudo xsane-find-scanner - only the webcams are detected
Have edited /etc/sane.d/epson2.conf - added scanner usb ID, and added the lines:- usb /dev/usb/scanner0
        usb /dev/usbscanner0
as advised in one of the threads in this forum (sorry seen too many a
& cannot remember which one)

sudo scanimage -L gave this-
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `v4l:/dev/video1' is a Noname Creative Labs Webcam Pro Ex virtual device
device `v4l:/dev/video0' is a Noname Logitech QuickCam Pro 4000 virtual device


lsusb produced this list -
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 2222:3061 MacAlly 
Bus 002 Device 003: ID 1e54:2030  
Bus 002 Device 002: ID 05e3:0607 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04b4:1002 Cypress Semiconductor Corp. CY7C63001 R100 FM Radio
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 050d:0271 Belkin Components 
Bus 001 Device 007: ID 07ab:fcdf Freecom Technologies 
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 2001:f103 D-Link Corp. [hex] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 041e:4011 Creative Technology, Ltd WebCam PRO eX
Bus 003 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsmod -
listed no 
usb-ohci
usbcore
scanner

Following Scanner HOW TO ([http://tldp.org/HOWTO/Scanner-HOWTO/interfaces.html](http://tldp.org/HOWTO/Scanner-HOWTO/interfaces.html))
sudo ls -R /lib/modules/2.6.31-20-generic/kernel/drivers -
listed neither of the expected modules under usb
scanner.o
usbcore.o

however,  wusbcore was listed

A file search showed that scanner.o is located in /usr/lib/gap/bin (as with my working 9.04)
A file search for usbcore.o found nothing.

lspci -V listed my USB controller using "memory at.." which I understand means it is an OHCI controller.

cat /proc/filesystems did not list usbfs or usbdevfs 

Does this mean I need to mount the usbfs?
I tried the command (provided by another link) -
mount -t usbfs none /proc/bus/usb gave    - 
mount: mount point /proc/bus/usb does not exist

Searching the /proc/bus/ directory lists two subdirectories - input & pci.
Same search on the 9.04 machine shows the same 2 plus usb

I have also "browsed the kernel module list" (director@office:/usr/src/linux-headers-2.6.31-20$ sudo make menuconfig. repeated in linux-headers-2.6.31-20-generic as well) to see if I could see any usb modules to load -
Device Drivers | USB support shows the following modules not loaded -
USB device filesystem (DEPRECATED)
USB device class-devices (DEPRECATED)

the following had [*] -
EHCI HCD (USB2.0) support
OHCI HCD support
UHCI HCD (most Intel & VIA) support

Do I need to select M for these three modules?

the following had [M] -
USB Printer support
Microtek X6USB scanner support

It looks like the scanner module has not been loaded, and possibly the usbfs yet usb webcam and card readers are accessible.


I have tried to keep outputs relevant & short. If I have omitted anything, you would like full results or any other information. please let me know.


I would be very grateful for any advice to point me in the right direction to get my scanner working

Many thanks in advance

---

### Post by sisco311 on 2010-03-08
Try to install iscan:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

---

