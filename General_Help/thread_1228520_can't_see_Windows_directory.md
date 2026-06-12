---
title: "can't see Windows directory"
date: 2009-08-01
forum: General Help
---

### Post by ilikefire12 on 2009-08-01
I can't get into my Windows directory from my computer through Linux. Is there a way to fix this? or is that how its supposed to be?

---

### Post by doas777 on 2009-08-01
if you go to Places -> Computer, do you see your windows partition shown there? you can 
doubleclick it to mount the drive for access.

if you can't find it there, please run this command in terminal and post the output
```
sudo fdisk -l
```

---

### Post by ilikefire12 on 2009-08-01
I don't see it in there at all. 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d790797

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37207   298859520    7  HPFS/NTFS
/dev/sda2           37207       38913    13707264    7  HPFS/NTFS

---

### Post by doas777 on 2009-08-01
are you on a live cd?

if so, try opening a terminal and pasting in these commands:
```

sudo mkdir /media/disk1
sudo mkdir /media/disk2
sudo mount -t ntfs /dev/sda1 /media/disk1
sudo mount -t ntfs /dev/sda2 /media/disk2

```

then if you navigate an nautilus window (the file manager) to /media/diskx and you should see your files.

---

### Post by ilikefire12 on 2009-08-01
No I'm not on a LiveCD. I have Ubuntu installed in a file in Windows that lets me dual boot.

---

### Post by doas777 on 2009-08-01
really? in that case, i don;t know if there is any way to do that. give the commands a try though. who know, might work.

---

### Post by ilikefire12 on 2009-08-01
This is what it gave me.

The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

---

### Post by ad_267 on 2009-08-01
Do you mean you installed using Wubi? If so I believe you can access your Windows drive from /host

---

### Post by ilikefire12 on 2009-08-01
Yeah I guess it was Wubi. I forgot was it was called. And the last commands I used seem to have gave me access to Windows files.

---

