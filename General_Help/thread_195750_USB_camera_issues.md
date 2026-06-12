---
title: "USB camera issues"
date: 2006-06-13
forum: General Help
---

### Post by JorgeMataleo on 2006-06-13
Running Dapper, I am trying to get access to the pictures on my digital camera.  It's a late-model camera (Canon Digital Ixus 800IS) that the usual apps don't recognize (gtkam, gphoto2, the one that automatically comes up when you plug your camera into the USB port (gthumb?)...)  

I would like to just mount it somewhere, but I can't find which device to mount from- there's no /dev/usb/, /dev/ubX, or /dev/sdX, which I thought were the usual suspects.  Here's the relevant entry for /proc/bus/usb/devices:-

T:  Bus=05 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04a9 ProdID=3119 Rev= 0.02
S:  Manufacturer=Canon Inc.
S:  Product=Canon Digital Camera
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=64ms

And here's what the system log says when I plug it in:-

 Jun 13 12:40:29 localhost kernel: [4372675.073000] usb 5-8: new high speed USB device using ehci_hcd and address 8

Any ideas on how to get at the pictures, or where to mount from?

TIA

---

### Post by barthel on 2006-06-13
I've got 2 answers for you--quick and long.

Here's the quick answer:

USB devices have SCSI nodes under /dev.

Look for /dev/sda /sda1, etc.

The long answer would be to set up a custom set of udev rules to define a fixed symlink, since USB devices aren't guaranteed to get the same device node each time.

I use ```
udevinfo -a -p $(udevinfo -q path -n /dev/sda)
``` to pull up the attributes for a device node (in this case /dev/sda).

Then, using the attributes from a single block of the output, I create the udev rules. Here's the current contents of my **/etc/udev/rules.d/01-trippant.rules** ('trippant' is my machine name):
```
# USB floppy drive
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="MITSUMI USB FDD", SYMLINK=="ufa"

# WDC 880BB USB drive...
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="Western Digital USB Hard Drive", SYSFS{serial}=="AC030714020331", SYMLINK="uda%n"

# 3.5" external USB hard drive enclosure...
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="USB2.0 Storage Device", SYSFS{serial}=="DEF1FE27ED9DCDEF", SYMLINK="udb%n"

# 2.5" external USB hard drive enclosure...
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="USB2.0 Storage Device", SYSFS{serial}=="DEF1093F9404", SYMLINK="udc%n"

# W@LK KEY USB flash drive
# NOTE: The old product string is gone--had to resort to the id numbers.
#   BUT--it's WORKING for the first time since I bought it!!!
BUS=="usb", KERNEL=="sd*", SYSFS{idProduct}=="0005", SYSFS{idVendor}=="0c76", SYMLINK="flash"

# Nikon CoolPix digital camera (thank you Christine!)
BUS=="usb", KERNEL=="sd*", SYSFS{manufacturer}=="NIKON", SYSFS{serial}=="000030697413", SYMLINK="camera"

```

[http://www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html") is a good reference.

Some may see this as overkill, given the features of HAL, but I've been doing it this way for years to give me fixed mount points for removable devices. Plus, I'm not happy with the way  HAL (or gnome-volume-manager or some other software in the automounting chain) names my devices. Since I can use my "fixed" symlinks in /etc/fstab, it allows me a lot more flexibility with tools like GKrellm and my own shell scripts.

HTH

---

