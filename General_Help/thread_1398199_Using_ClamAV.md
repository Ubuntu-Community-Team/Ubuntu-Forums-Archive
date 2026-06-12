---
title: "Using ClamAV"
date: 2010-02-04
forum: General Help
---

### Post by Rick Abraham on 2010-02-04
Hi guys I have installed Ubuntu onto a USB pendrive and Im using it to scan my mates Windows PC for malware etc.
He is running 2 hard drives to scan the first drive I used the command

clamscan -r --bell --remove=yes /media/disk

and that worked, now the second drive is listed as System Drive but when I put this command in it didnt work

clamscan -r --bell --remove=yes /media/system drive

it tells me that it cannot access the file /media/system and
/media/system is no such file or directory

what would be the mount name for the second drive ????
Any help would be great

---

### Post by Rick Abraham on 2010-02-04
Is there a command I can type in the terminal that lists all drives mounted and there correct mount names.
Obviously when you are in the Gnome GUI the mount names they use are not what ClamAV uses.

---

### Post by Leppie on 2010-02-04
> **Rick Abraham said:**
> Hi guys I have installed Ubuntu onto a USB pendrive and Im using it to scan my mates Windows PC for malware etc.
He is running 2 hard drives to scan the first drive I used the command

clamscan -r --bell --remove=yes /media/disk

and that worked, now the second drive is listed as System Drive but when I put this command in it didnt work

clamscan -r --bell --remove=yes /media/system drive

it tells me that it cannot access the file /media/system and
/media/system is no such file or directory

what would be the mount name for the second drive ????
Any help would be great
there's 2 ways to solve this, either you use quotes for the path to the destination drive:
```
clamscan -r --bell --remove=yes "/media/system drive"
```
or you have to escape the space:
```
clamscan -r --bell --remove=yes /media/system\ drive
```

hope this helps

---

### Post by Leppie on 2010-02-04
> **Rick Abraham said:**
> Is there a command I can type in the terminal that lists all drives mounted and there correct mount names.
Obviously when you are in the Gnome GUI the mount names they use are not what ClamAV uses.
to list everything mounted:
```
sudo mount -l
```

hope this helps

---

### Post by Rick Abraham on 2010-02-04
Hi thanks for the reply.
I tried both those commands and the same result it cannot find the drive

---

### Post by Leppie on 2010-02-04
then what is the output of
```
sudo mount -l
```

---

### Post by Rick Abraham on 2010-02-04
Hi I executed the following command sudo mount -l
and it showed my 2 internal drives

/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) []
/dev/sda1 on /media/System Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [System Drive]

I cannot understand why

/media/disk       
works but
/media/system drive
doesnt when its listed above as that ?????????????????????????????

---

### Post by howefield on 2010-02-04
Try capitalising.

System Drive might be different to system drive.

---

### Post by Leppie on 2010-02-04
> **Rick Abraham said:**
> Hi I executed the following command sudo mount -l
and it showed my 2 internal drives

/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) []
/dev/sda1 on /media/System Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [System Drive]

I cannot understand why

/media/disk       
works but
/media/system drive
doesnt when its listed above as that ?????????????????????????????
remember that linux is always case sensitive unless you issue a command that supports a switch for case insensitive functionality. hence the correct command should be:
```
clamscan -r --bell --remove=yes /media/System\ Drive
```

---

### Post by Rick Abraham on 2010-02-04
Thanks Leppie this command worked, I forgot to use capitals

clamscan -r --remove=yes /media/System\ Drive

---

### Post by Leppie on 2010-02-04
> **Rick Abraham said:**
> Thanks Leppie this command worked, I forgot to use capitals
you're welcome :)

if this is solved, please use the thread tools to set it to solved.

---

### Post by ghostborg on 2010-02-04
I recently had a file that had a W32 trojan and Clam fully updated would not detect it. I then installed Avast for Linux and that detected it.

I discovered this file when I tried to copy the file to a Windows machine and it refused it.

I wish they would come out with better products for Linux, most of the stuff is like Alpha at best. The scanners are like from the Win 3.1 era.

---

### Post by Leppie on 2010-02-04
i'm not sure how you use your av, but the avast one should use the same definitions as their windows version.
maybe all you had to do before scanning was updating the av?

---

