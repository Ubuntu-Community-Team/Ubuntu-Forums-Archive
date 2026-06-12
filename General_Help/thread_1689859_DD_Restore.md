---
title: "DD Restore"
date: 2011-02-17
forum: General Help
---

### Post by Cooper88 on 2011-02-17
Whenever I do a DD restore from a raw forensics image I am unable to mount the volumes. DD says I have no errors and 100 gigs have been writen but I can't access the window drives. 
 
I have two images and both do the same thing and my counter parts says they have no problems viewing the files. 
 
The command I'm using is 
 
dd if=/media/sdc2/QCE3_1/QCE3_1.001 of="dev/sdb"
 
sdb is the new drive i purchased and QCE3 is a multifile DD image. Thanks for your help.
 
I'm running a testdisk on the drive but I'm getting a warning, "Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD) and I'm thinking I have to add more flags to my restore?

---

### Post by earthmeLon on 2011-02-17
> **Cooper88 said:**
>  
dd if=/media/sdc2/QCE3_1/QCE3_1.001 [COLOR="Red"]of="dev/sdb"[/COLOR]


Have you tried:
```

dd if=/media/sdc2/QCE3_1/QCE3_1.001 [COLOR="Green"]of=/dev/sdb
[/COLOR]

```

Also, you may have to tell it which partition of sdb you want to place it:  such as sdb1, sdb3, sdb5, whatever.

Goodluck.  Let me know if it works out :D

---

### Post by Cooper88 on 2011-02-18
root@cooper-desktop:/media/sdb1# mmls -t dos /media/sdc2/QCE3_1/QCE3_1.???DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

Slot Start End Length Description
00: Meta 0000000000 0000000000 0000000001 Primary Table (#0)
01: ----- 0000000000 0000002047 0000002048 Unallocated
02: 00:00 0000002048 0152203255 0152201208 NTFS (0x07)
03: ----- 0152203256 0152203263 0000000008 Unallocated
04: 00:01 0152203264 0156299263 0004096000 NTFS (0x07)
05: ----- 0156299264 0156301505 0000002242 Unallocated


root@cooper-desktop:/media/sdb1# sudo mount -t ntfs-3g -o ro,loop,show_sys_files,offset=1048576 /media/sdc2/QCE3_1/QCE3_1.001 /media/sdb1/DATA/
Failed to read last sector (152201207): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
or it was not setup correctly (e.g. by not using mdadm --build ...),
or a wrong device is tried to be mounted,
or the partition table is corrupt (partition is smaller than NTFS),
or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
 
---------------
My dd image is a 2g mulitfile. Do I need to combine the image first to mount the partition?

---

### Post by The Cog on 2011-02-18
I'm guessing that something in the image partition table indicates a disk geometry (e.g. number of heads) that doesn't match the new physical disk.

Your attempt to mount the partition looks OK, but I think you need to join the parts together tho make a single file containing the whole partition before you can expect it to mount.

---

### Post by Cooper88 on 2011-02-19
wow you are correct, I had to merge the files before running the command above. 
 
cat dd_.* > fullimage.dd
 
Once I did that I was able to mount the image. What a waste of time. I think I had the same issue a few years ago. And I asked this same question why?

---

### Post by The Cog on 2011-02-19
Yes! The boy's on fire!

It was a guess, but the clue is in the error message you posted:
> Failed to read last sector (152201207)
That matches the sector numbers in the partition table you posted, as the last sector. Why it wants to read the last sector, I don't know. But until you join them all together it won't be able to because the file is too short.

---

