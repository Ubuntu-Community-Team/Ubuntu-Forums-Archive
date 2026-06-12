---
title: "cant get udev rules for USB syc to work"
date: 2009-09-04
forum: General Help
---

### Post by chrisbay90 on 2009-09-04
I want to be able to automatically synchronize some a folder on my USB thumb drive with a folder on my local drive, whenever i plug it in.

I started following this [http://www.linuxjournal.com/article/9311](http://www.linuxjournal.com/article/9311) tutorial. At least the part that runs a script automatically when a certain device is mounted and planned to just make my script an rsync one liner.

However i can't seem to get the udev rules to work. So far i just have a bash script that plays a tone so i know the udev event rule has fired. But it doesnt seem run when i plug in my thumb drive.

This is the output of cat /proc/scsi/usb-storage/*

```
cat /proc/scsi/usb-storage/*
   Host scsi10: usb-storage
       Vendor: TOSHIBA
      Product: TransMemory     
Serial Number: 0141CB70B3316941
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:
```I then created a file at /etc/udev/rules.d called 95.test.rules with the contents:
```
BUS="usb", SYSFS{serial}="0141CB70B3316941", SYMLINK="TOSHIBA", RUN+="/usr/local/bin/usbTest.sh"
```and the files /usr/local/bin/usbTest.sh has the contents:
```
#!/bin/bash

SOUND=/usr/share/sounds/card_shuffle.wav

aplay ${SOUND} > /dev/null 2>&1
```For the time being i just have it play a sound so i know the event rule is working.

running the above files directly works. But plugging in the usb drive does not play a sound.

Any suggestions would be appreciated.

---

### Post by chrisbay90 on 2009-09-05
bump.

---

### Post by Micaelus on 2009-09-09
I am having the same problem. I'm running Jaunty x64 and have seemingly tried every combination of udev rules and commands I can imagine after visiting a number of tutorials, all producing no results. I followed the guides from [http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)  as well as [http://www.linuxjournal.com/article/9311](http://www.linuxjournal.com/article/9311)  and this one too [http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/) all to no avail. 

The specific rules I attempted included, but are not limited to, the following:
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="058f", SYSFS{idProduct}=="6387", RUN+="/usr/local/usb_sync"

ACTION=="add", SUBSYSTEMS=="usb", ATTRS{idVendor}=="058f", ATTRS{idProduct}=="6387", ATTRS{manufacturer}=="JetFlash", ATTRS{product}=="Mass Storage Device",  RUN+="/usr/local/usb_sync"

ACTION=="add", SUBSYSTEMS="scsi", ATTRS{vendor}=="JetFlash", ATTRS{model}=="Transcend 1GB   ", RUN+="/usr/local/usb_sync"

ACTION=="add", SUBSYSTEMS=="usb", ATTRS{idVendor}=="058f", ATTRS{idProduct}=="6387", RUN+="/usr/local/usb_sync"

ACTION=="add", BUS=="usb", SYSFS{serial}=="14CA8GWC", RUN+="/usr/local/usb_sync"

I've exchanged SYSFS for ATTRS, ran various identifying commands and tried to ID my flash drive any way I could, but it never runs the script when I insert the drive. (The script is executable and works properly when I run it from Nautilus or the terminal. It even includes a 'sleep 10' to wait for the thumb drive.) Any insights would be appreciated.

---

