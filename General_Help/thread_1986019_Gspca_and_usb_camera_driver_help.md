---
title: "Gspca and usb camera driver help"
date: 2012-05-24
forum: General Help
---

### Post by harshasunder on 2012-05-24
Ive got a usb camera from a company called videology, and they sent me a linux driver for the camera.It requires gspca , but since im using ubuntu 11.04 I know its already on my comp, so i didnt reinstall it. Now the problem  is that after installing the driver, my camera is still not getting recognized. These are the outputs of some commands:

lsusb utility gave the following result

###########################################################################
[root@localhost linux-2.6.29.4]# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1bbd:0043
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

###########################################################################

The desktop i currently use runs linux (ubuntu 11.04 32 bit system)

 lsmod displays the kernel objects as shown below.
#########################################################################
[root@localhost linux-2.6.29.4]# lsmod |grep gspca
gspca_videology_24B    13402  0
gspca_main             27894  1 gspca_videology_24B
videodev               75143  1 gspca_main

########################################################################

dmesg utility gave the following result:

#########################################################################
[85897.697182] Linux video capture interface: v2.00
[85897.706969] gspca: v2.12.0 registered
[87355.872924] usbcore: registered new interface driver gspca_videology_24B
[87355.872930] gspca_videology_24B: registered
[87517.432028] usb 1-3: new high speed USB device using ehci_hcd and address 2
[87885.439628] usbcore: deregistering interface driver gspca_videology_24B
[87885.439676] gspca_videology_24B: deregistered
[87915.512838] usb 1-3: USB disconnect, address 2
[87918.328022] usb 1-3: new high speed USB device using ehci_hcd and address 3
[87936.132565] Linux video capture interface: v2.00
[87936.137694] gspca: v2.12.0 registered
[87951.189323] usbcore: registered new interface driver gspca_videology_24B
[87951.189327] gspca_videology_24B: registered
[88213.041529] usb 1-3: USB disconnect, address 3
[88222.224021] usb 1-3: new high speed USB device using ehci_hcd and address 4

###########################################################################

And last but not the least, /dev/video0 does not exist

So it can be seen that there is some fault on the driver registration side or device recognition. 
Is there any suggestion that someone has to get it working? Shouldnt dmesg have subsequent steps?On another page ([https://bbs.archlinux.org/viewtopic.php?id=112916),someone](https://bbs.archlinux.org/viewtopic.php?id=112916),someone) else has posted the output of these commands and I noticed that there output for dmesg was :
#########################################################################
usb 4-1: new full speed USB device using uhci_hcd and address 2
usb 4-1: New USB device found, idVendor=0ac8, idProduct=303b
usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 4-1: Product: PC Camera
usb 4-1: Manufacturer: Vimicro Corp.
usb 4-1: configuration #1 chosen from 1 choice
Linux video capture interface: v2.00
gspca: main v2.5.0 registered
gspca: probing 0ac8:303b
zc3xx: probe 2wr ov vga 0x0000
zc3xx: probe 3wr vga 1 0xe001
zc3xx: probe sensor -> 0013
zc3xx: Find Sensor MI0360. Chip revision e001
gspca: probe ok
usbcore: registered new interface driver zc3xx
zc3xx: registered
usbcore: registered new interface driver gspca
gspca driver 01.00.20 registered
##########################################################################

any idea why im not getting this??
long post. sorry if it was not too coherent

harsha

---

