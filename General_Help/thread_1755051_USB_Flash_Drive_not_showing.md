---
title: "USB Flash Drive not showing"
date: 2011-05-10
forum: General Help
---

### Post by jchw on 2011-05-10
I use a flash drive for regular back up and other work and this has been very successful until two days ago.

None of my USB flask drives are showing in the Places menu when I connect them. I have a dual boot with Mint and they work perfectly in Mint.

A few days ago I was unsuccessfully trying to get my Broadcom wifi card to work and was following threads to install and uninstall various firmware programs. I am not sure if this caused the loss of the USB drive.

When I go into System Profiler and Benchmark nothing is showing under USB devices.

Does anyone have any ideas how I may be able to get my USB drives back?

---

### Post by TheNerdAL on 2011-05-10
In a terminal use

```
lspci
```

then 

```
lsusb
```

---

### Post by layers on 2011-05-10
Is there any difference between the outputs of ```
sudo fdisk -l
```
from before you plug in the USB, and after you plug in the USB?

---

### Post by jchw on 2011-05-10
Here is the output from lspci:

john@john-eMachines-E525:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
john@john-eMachines-E525:~$ 


Here is the output from lsusb:

john@john-eMachines-E525:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0930:6533 Toshiba Corp. 512M Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
john@john-eMachines-E525:~$ 

And here is the difference between fdisk with the USB connected and then removed.
john@john-eMachines-E525:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035219

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       42648   342561146+  83  Linux
/dev/sda2           49853       60802    87944193    5  Extended
/dev/sda5           59655       60802     9212928   82  Linux swap / Solaris
/dev/sda6           49853       50285     3472384   82  Linux swap / Solaris
/dev/sda7           59250       59654     3249152   82  Linux swap / Solaris
/dev/sda8           50286       58878    69022720   83  Linux
/dev/sda9           58879       59249     2978816   82  Linux swap / Solaris

Partition table entries are not in disk order
john@john-eMachines-E525:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035219

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       42648   342561146+  83  Linux
/dev/sda2           49853       60802    87944193    5  Extended
/dev/sda5           59655       60802     9212928   82  Linux swap / Solaris
/dev/sda6           49853       50285     3472384   82  Linux swap / Solaris
/dev/sda7           59250       59654     3249152   82  Linux swap / Solaris
/dev/sda8           50286       58878    69022720   83  Linux
/dev/sda9           58879       59249     2978816   82  Linux swap / Solaris

Partition table entries are not in disk order
john@john-eMachines-E525:~$ 

Hopefully this helps diagnose the problem,

Many thanks

---

### Post by layers on 2011-05-10
And none of these are the USB?```
dev/sda1   *           1       42648   342561146+  83  Linux
/dev/sda2           49853       60802    87944193    5  Extended
/dev/sda5           59655       60802     9212928   82  Linux swap / Solaris
/dev/sda6           49853       50285     3472384   82  Linux swap / Solaris
/dev/sda7           59250       59654     3249152   82  Linux swap / Solaris
/dev/sda8           50286       58878    69022720   83  Linux
/dev/sda9           58879       59249     2978816   82  Linux swap / Solaris
```

---

### Post by jchw on 2011-05-10
No, none of these are USB's.

---

### Post by jchw on 2011-05-10
I should add that sda1 contains Ubuntu which is my main OS and I have Mint in sda8. All the other partitions are extended or swap partitions.

---

### Post by layers on 2011-05-10
Never had a problem like this one. Usually, everything is in fdisk -l, but not in places. This is what I would do:

Try going to Applications -> Ubuntu Software  Center. In the search bar type in "usb" without the quotes. Install the  package, "usbmount" After it installs plug in your USB drive and it  should be all set up.

Also, try plugging the USB and running fdisk -l after like a minute after, to make sure that you cannot see anything. Remove other USB devices, such as mouses (mice, idk is it mice for a mouse as a computer device; if it is, then would laptops have multiple micepads or mousepads...???)

Hope this helps! Let me know how it turns out.

---

### Post by jchw on 2011-05-11
I have installed usbmount using Synaptic Package Manager but I cannot see where this appears in the Main Menu. Do you know how to access the program?

When I connect the USB drive it flashes green and then the light immediately goes out so I suspect the problem is the driver. The mouse works in the same USB slot so it is not a hardware problem. I tried  fdisk -l but it did not make any difference.

If I can get usbmount working I think it will correct the problem. 

Many thanks for the help.

---

### Post by sidzen on 2011-05-11
[http://www.pane-free.com/pg_2.html](http://www.pane-free.com/pg_2.html)

---

### Post by RJ12 on 2011-05-11
Try this in the terminal

```
sudo modprobe usb-storage
```

I have this problem because of NDISwraper (Windows Wireless Drivers)

---

### Post by jchw on 2011-05-11
Here is the output from the command I picked up from pane-free.com and then I tried running sudo modprobe usb-storage.


john@john-eMachines-E525:~$ sudo ls -l /dev/disk/by-id/*usb* 
[sudo] password for john: 
ls: cannot access /dev/disk/by-id/*usb*: No such file or directory
john@john-eMachines-E525:~$ sudo modprobe usb-storage
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
john@john-eMachines-E525:~$ 

I am not sure what this means. When I was trying to get the wifi card working a few days ago is it possible I have blacklisted the USB drive or deleted the driver? The USB drive was fine until around that time. I have checked Ndiswrapper and it is not installed although I have installed it and reinstalled it many times over the last few months trying to get the wifi card working.

Sorry about my lack of knowledge on this but this is pushing my IT skills to their limits.

---

### Post by jchw on 2011-05-12
After trying all suggestions to resolve this I went into Unetbootin yesterday and downloaded 11.4. I then went to Administration, create start up disc and surprise, surprise the flash drive worked. The memory stick icon appeared on the desktop and the drive showed under Places. I then created a bootable stick and loaded 11.4.

Today I tried again and after booting up my laptop the USB drive is no longer working so it was obviously a one off fix. The underlying problem still exists. 

Any thoughts on how to get the USB drives working again would be appreciated.

---

### Post by jchw on 2011-05-12
john@john-eMachines-E525:~$ sudo modprobe usb-storage
[sudo] password for john: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
john@john-eMachines-E525:~$ 

Does this mean that I have by mistake blacklisted my USB drive which is why it is not working? Is so how would I rectify this?

Any thoughts appreciated.

---

### Post by jchw on 2011-05-13
Finally I have solved the problem.

It was indeed caused because I blacklisted my USB drive when I was following a post on how to get my Broadcom 4312 wifi card working.

I ran sudo gedit /etc/modprobe.d/blacklist in the terminal, came up with the blacklist, deleted each entry and rebooted. All my memory sticks are now working. The wifi card still does not work but I have got used to that.

The lesson learnt is not to follow posts when I do not understand the potential dangers.

Many thanks to all for support and guidance.

---

### Post by sidzen on 2011-05-14
Good job!    :D
Welcome to the fun of Linux!

---

