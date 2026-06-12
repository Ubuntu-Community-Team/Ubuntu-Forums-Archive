---
title: "Device ID"
date: 2010-08-20
forum: General Help
---

### Post by Brannyh on 2010-08-20
How do you find the device node for a USB drive in Kubuntu.

---

### Post by ankspo71 on 2010-08-20
Hi,
Try pasting these commands into Konsole/terminal after the device is plugged in (and turned on if necessary). One of these should give you the info you are looking for. 

```
sudo fdisk -l
```
List all of your disks and shows the device names and partition info. 

```
sudo blkid
```
Shows you the UUIDs and device names of all the disks.

```
sudo lshw
```
Lists all hardware and their info.

Hope this helps.

---

### Post by Zeike on 2010-08-21
actually what I think you're looking for is the 'lsusb' command.

You can add the '-v' switch to it to get more info.

---

