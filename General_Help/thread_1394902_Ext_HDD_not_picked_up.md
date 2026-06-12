---
title: "Ext HDD not picked up"
date: 2010-01-31
forum: General Help
---

### Post by mario.r on 2010-01-31
I'm new to Linux and have a Netbook with Ubntu 8.10 installed on it and Gnome 2.24.1.

When I plug in a flash drive into the USB port it picks it up but when I plug in my 2.5" 500gb external drive then nothing is picked up.  It is formatted as NTFS and picked up on my Windows PCs...is there anything I need to do on Ubuntu to get it picked up?

---

### Post by blueshiftoverwatch on 2010-01-31
Check /*media* and see if by any chance it shows up in there.

---

### Post by mario.r on 2010-01-31
/media folder contains cdrom and floppy folders.  No folder for ext HDD.  

Any other ideas?

---

### Post by wojox on 2010-01-31
Try manually mounting: [https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting](https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting)

---

### Post by spiky001 on 2010-01-31
There was a post earlir today take a look 
[http://ubuntuforums.org/showthread.php?t=1394190](http://ubuntuforums.org/showthread.php?t=1394190)

---

### Post by jbiggs12 on 2010-01-31
> when I plug in my 2.5" 500gb external drive then nothing is picked up.

Does it show up under GParted/Disk Utility?

---

### Post by mario.r on 2010-01-31
Checked the link sent, when I do a "sudo fdisk -l" without the Ext HDD attached, I get 3 entries:
Device               System
/dev/sda1          Linux
/dev/sda2          Extended
/dev/sda3          Linux Swap / Solaris

When I do the same with the Ext HDD plugged in, I get the same 3 entries from the above command...any ideas?

---

### Post by mario.r on 2010-01-31
> **spiky001 said:**
> There was a post earlir today take a look 
[http://ubuntuforums.org/showthread.php?t=1394190](http://ubuntuforums.org/showthread.php?t=1394190)
Thanks, I checked the other thread but when I do a df -h I still don't see my 500gb HDD...?

---

### Post by wdr on 2010-01-31
> **mario.r said:**
> Thanks, I checked the other thread but when I do a df -h I still don't see my 500gb HDD...?
By chance is this a WD Passport. If so these drives require a specific driver in XP.
They are a pain in XP and I imagine the same in Ubuntu.

---

### Post by mario.r on 2010-01-31
No, Samsung HDD

---

### Post by SecretCode on 2010-01-31
Post the output of *lsusb* without the drive plugged in and again with it plugged in.

Have a look at System > Administration > Log File Viewer and check if any messages appear in 'messages' or 'syslog' when you attach the drive.

---

