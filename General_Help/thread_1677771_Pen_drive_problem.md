---
title: "Pen drive problem"
date: 2011-01-29
forum: General Help
---

### Post by L Style on 2011-01-29
when i plug 4GB & 8Gb pen drives ubuntu 10.04 doesn't work with that. any one knows how to fix this. 

 achitha@lachitha-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1613 Kingston Technology DataTraveler 8GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub:confused::confused::confused::confused::confused::confused::confused:

---

### Post by ajgreeny on 2011-01-29
What exactly do you mean by doesn't work?  The 8GB one you have shows in lsusb, so it is seen by the system.  Is the problem that it does not automount?

---

### Post by L Style on 2011-01-29
> **ajgreeny said:**
> What exactly do you mean by doesn't work?  The 8GB one you have shows in lsusb, so it is seen by the system.  Is the problem that it does not automount?

yeah that's the problem

---

### Post by TheHackOps on 2011-01-29
Add it to fstab

---

### Post by L Style on 2011-01-29
> **TheHackOps said:**
> Add it to fstab

how can i do that i'm new to ubuntu

---

### Post by ajgreeny on 2011-01-29
Fstab may not be the best way.
First open up a terminal from the Applications-Accessories menu, type in there ```
sudo blkid
``` to see if the drive has a label, which many do by default.  Post back here if you're not sure.  If it appears to have a label, make a note of it; it will look something like:-
/dev/sdb1: LABEL="KINGSTON" UUID="7A5C-FB4C" TYPE="vfat"
if it is labeled, ie in my case KINGSTON, you can make a folder to mount it with ```
sudo mkdir /media/KINGSTON
```using your own label.  Now use command ```
sudo mount /dev/sdb1 -t vfat /media/KINGSTON
```making sure you get the /dev/sdb1 correct, and the /media/label folder correct as well.

That should mount the disk, and you may find from then on that it mounts automatically.

---

### Post by L Style on 2011-01-29
> **ajgreeny said:**
> Fstab may not be the best way.
First open up a terminal from the Applications-Accessories menu, type in there ```
sudo blkid
``` to see if the drive has a label, which many do by default.  Post back here if you're not sure.  If it appears to have a label, make a note of it; it will look something like:-
/dev/sdb1: LABEL="KINGSTON" UUID="7A5C-FB4C" TYPE="vfat"
if it is labeled, ie in my case KINGSTON, you can make a folder to mount it with ```
sudo mkdir /media/KINGSTON
```using your own label.  Now use command ```
sudo mount /dev/sdb1 -t vfat /media/KINGSTON
```making sure you get the /dev/sdb1 correct, and the /media/label folder correct as well.

That should mount the disk, and you may find from then on that it mounts automatically.

It's not work friend, Pen drive not in the terminal  

lachitha@lachitha-desktop:~$ sudo blkid
/dev/sda1: UUID="cca47391-3cbb-4525-a17a-6838db02a25c" TYPE="ext4" 
/dev/sda5: LABEL="MEDIA" UUID="C229-3FF5" TYPE="vfat" 
/dev/sda6: LABEL="STUFF" UUID="3C1A-29BD" TYPE="vfat" 
/dev/sda7: LABEL="MUSIC" UUID="F887-6172" TYPE="vfat" 
/dev/sda8: UUID="dcb8af82-0ac2-41f0-8744-819c440b57fe" TYPE="swap" 
lachitha@lachitha-desktop:~$

---

### Post by L Style on 2011-01-29
In dmesg I got this

[ 5315.070358] usb 1-6: configuration #1 chosen from 1 choice
[ 5315.076437] scsi15 : SCSI emulation for USB Mass Storage devices
[ 5315.078459] usb-storage: device found at 6
[ 5315.078467] usb-storage: waiting for device to settle before scanning
[ 5331.855471] usb 1-6: USB disconnect, address 6
[ 5334.144050] usb 1-6: new high speed USB device using ehci_hcd and address 7
[ 5334.287966] usb 1-6: configuration #1 chosen from 1 choice
[ 5334.292436] scsi16 : SCSI emulation for USB Mass Storage devices
[ 5334.298765] usb-storage: device found at 7
[ 5334.298774] usb-storage: waiting for device to settle before scanning

---

### Post by L Style on 2011-01-30
bump

---

