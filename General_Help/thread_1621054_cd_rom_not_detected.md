---
title: "cd rom not detected"
date: 2010-11-13
forum: General Help
---

### Post by status1 on 2010-11-13
Hello,
I installed Ubuntu 10.04 and I am just starting out using it
I wanted to play a music cd but it doesn't work After doing some checking I find that the cdrom is not mounted
Does the cdrom has to be mounted manually or is that supposed to be mounted automatically at each boot ?
I have Ubuntu dual booting with windows xp  and the cdrom is detected and plays with xp so the cdrom itself is working
Also I did not have any problems installing Ubuntu from the live cd but after it's installed now it doesn't detect or mount the cdrom
How can that be ?
Is there anything I can check to troubleshoot this problem ?

---

### Post by dcstar on 2010-11-13
> **status1 said:**
> Hello,
I installed Ubuntu 10.04 and I am just starting out using it
I wanted to play a music cd but it doesn't work After doing some checking I find that the cdrom is not mounted
Does the cdrom has to be mounted manually or is that supposed to be mounted automatically at each boot ?
I have Ubuntu dual booting with windows xp  and the cdrom is detected and plays with xp so the cdrom itself is working
Also I did not have any problems installing Ubuntu from the live cd but after it's installed now it doesn't detect or mount the cdrom
How can that be ?
Is there anything I can check to troubleshoot this problem ?

Is the CD drive a SATA device (small data cable) or an old IDE (wide data cable) device?

If it is an IDE device on its own cable and set to Slave, then try changing it to Master.

---

### Post by status1 on 2010-11-14
I have an old IDE cable and it's on it's own and it was set to slave
I changed it to master but I still don't see it listed
I verified with xp that it re detected the cdrom drive and it still works but I see no change under Ubuntu

---

### Post by dino99 on 2010-11-14
check:

- bios settings
- Applications -> system tools -> config editor

to know about that hardware

sudo update-usbids && sudo update-pciids

---

### Post by status1 on 2010-11-14
I don't have system tools under applications Perhaps it's not installed ?
I did find something else though under System/Administration?Disk utility
I see it is listed there I clicked on it and I found something that is probably why it's not working

It shows the connection as SCSI which I am sure it's not right and also the device as dev/sr0 which is probably because the connection is SCSI

I don't think I have any settings for SCSI in the bios so I am not sure how to fix that
Are those commands supposed to fix that or is that for something else ?
I tried them anyway but it didn't work It said command not found

---

### Post by status1 on 2010-11-20
Just to answer my own post here
The problem is solved. It has nothing to do with the cable setting master/ slave and the SCSI connection makes no difference either
Apparently Ubuntu does/not play audio cd's out of the box After reading some posts I tried a data cd and it worked then I talked to someone at work and he said I need an audio player and suggested VLC media player
I installed it and now I can play audio cd's

---

