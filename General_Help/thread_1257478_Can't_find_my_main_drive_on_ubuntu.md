---
title: "Can't find my main drive on ubuntu"
date: 2009-09-03
forum: General Help
---

### Post by thenoobguru on 2009-09-03
ok so i got ubuntu and im switching from vista, but my ubuntu is on my RECOVERY D:\ drive, and it cant find my C:\ drive is there anyway i can make it so it does, my D:\ only has a  1.19 GBs left.
thanks
thenoobguru

---

### Post by RedSingularity on 2009-09-03
In terminal type 

sudo fdisk -l

Check if you can see it there.

---

### Post by cdbitesky on 2009-09-03
Ubuntu automatically reads local NTFS drives. Did you format the C:\ drive? Are they on the same hard drive?

---

### Post by fluffman86 on 2009-09-03
Only Windows uses letters like C: and D: to reference drives.  For Ubuntu, the filesystem is all based on "/" the root of your system.  

To find your files or folders that were in Windows, go to Places and it should be listed there.  So if your C: drive in Windows was 60 GB, then you should see an entry for "60.0 GB Media."

---

### Post by thenoobguru on 2009-09-03
> **fluffman86 said:**
> Only Windows uses letters like C: and D: to reference drives.  For Ubuntu, the filesystem is all based on "/" the root of your system.  

To find your files or folders that were in Windows, go to Places and it should be listed there.  So if your C: drive in Windows was 60 GB, then you should see an entry for "60.0 GB Media."
oh, sorry ive never used linux until about an hour ago

---

### Post by thenoobguru on 2009-09-03
> **Shadow121 said:**
> In terminal type 

sudo fdisk -l

Check if you can see it there.
frank@ubuntu:~$ c:\
> open
bash: c:open: command not found
frank@ubuntu:~$ c:\users
bash: c:users: command not found
frank@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
frank@ubuntu:~$

---

### Post by fluffman86 on 2009-09-03
Don't be sorry, I was just helping to point that out so you could find your files.  :)

Did you find your drive under Places?  It's at the top of the screen next to Applications.

---

### Post by hockeytux on 2009-09-03
Yup go to Places > Computer and you should see your 'Filesystem' (in crude terms what would the C:/ drive in Windows)

If you double-click it you will see a slash as drive name. Thats it. :)

---

### Post by RedSingularity on 2009-09-03
Ohhh lol not fdisk -1

sudo fdisk -l (the letter L)

---

