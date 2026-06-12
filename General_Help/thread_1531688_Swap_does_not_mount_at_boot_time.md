---
title: "Swap does not mount at boot time"
date: 2010-07-15
forum: General Help
---

### Post by paulie420 on 2010-07-15
For some time now - every time I reboot my computer the swap drive is not mounting.  I have to manually mount (Swapon) it via GParted.  Using the sudo mount -a does not seem to have an effect.

can Anyone tell me what is going on

here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=216a046d-95f1-41b6-bf3f-9318f1aa6825 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=82f33897-627e-4989-a5d3-efb303ccb79d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//10.0.0.6/ppmuetze /media/paulstorage   cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//10.0.0.6/public   /media/publicstorage cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//10.0.0.206/echo2  /media/echo2         cifs credentials=/root/.smbecho,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//10.0.0.5/mridwg   /W                   cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

### Post by akakingess on 2010-07-15
I could be mistaken, but the swap partition doesn't need to be mounted, it is just used as a "page file" (to use a Windows term), but I don't think it has to actually be "mounted" in order to work. Hopefully, someone will chime in if I am mistaken.

---

### Post by plucky on 2010-07-15
Post output of ```
free -m
sudo blkid
``` before you turn on swap.The chances are that the UUID has changed and the swap partition is not being mounted.

---

### Post by mcduck on 2010-07-15
> **akakingess said:**
> I could be mistaken, but the swap partition doesn't need to be mounted, it is just used as a "page file" (to use a Windows term), but I don't think it has to actually be "mounted" in order to work. Hopefully, someone will chime in if I am mistaken.

It *does* have to be mounted , although it's of course not mounted into a directory like normal partitions are.

So yes, it has to be correctly defined in fstab for the system to be able to access and use it. (luckily, as Solaris filesystem has the same ID in the partition table as Linux swap, so if either OS tried to automatically use those partitions that could result in some nasty troubles... ;))

For the actual solution, I agree with plucky that most likely this problem is caused by having a wrong UUID in fstab, possibly as a result of formatting the swap partition at some point (any editing of partitions or formatting of filesystems within those partitions will change their UUIDs, so you always need to run the blkid command to check the new UUID and then fix fstab accordingly.).

---

### Post by akakingess on 2010-07-15
My mistake, I know it doesn't mount onto the desktop or anything and that is what I thought the OP was referring to, I know it has to be in FSTAB, but just misunderstood the question. Thanks for the clarification and helping the OP out.

---

