---
title: "check external harddisk on bootup"
date: 2010-06-06
forum: General Help
---

### Post by koenfloris on 2010-06-06
hi,

i got an external harddrive, i use for it for backups.

but... it gets corrupted every once in a while. how do i let kubuntu auto-check the harddisk for error's automatically?

its a 300gb harddisk using ext2, i am using kubuntu 10.04.

---

### Post by wieman01 on 2010-06-06
Hi, 

I believe you need a corresponding entry for the external drive in "/etc/fstab". Could you post the contents please? We'll go from there:
> cat /etc/fstab

---

### Post by wieman01 on 2010-06-06
Hi, 

I believe you need a corresponding entry for the external drive in "/etc/fstab". Could you post the contents please? We'll go from there:
> cat /etc/fstab

---

### Post by koenfloris on 2010-06-06
here are the contents of the fstab file
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1ca6e362-7b46-4fcb-9beb-d9455c71ff93 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f0d955e9-1c8e-4f94-8552-656d52f38df7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


these are my mounted partitions at the moment. "BackupDisk" is the external harddisk.

> /dev/sdb1 on /media/BackupDisk type ext2 (rw,nosuid,nodev,uhelper=hal)

/dev/sda1 on / type ext4 (rw,errors=remount-ro)


---

### Post by wieman01 on 2010-06-06
Looks fine. Last thing we need is the UUID. Please post the results of:
> sudo blkid

---

### Post by koenfloris on 2010-06-06
here they are:

> /dev/sda1: UUID="1ca6e362-7b46-4fcb-9beb-d9455c71ff93" TYPE="ext4" 
/dev/sda5: UUID="f0d955e9-1c8e-4f94-8552-656d52f38df7" TYPE="swap" 
/dev/sdb1: LABEL="BackupDisk" UUID="ae9195cd-a3c2-4128-ae92-14c53cdb83c1" TYPE="ext2" 

many thx 4 helping

---

### Post by wieman01 on 2010-06-07
Hi, 

You need to open this file:
> sudo gedit /etc/fstab
Then add these lines:
> # /media/BackupDisk on /dev/sdb1
UUID=ae9195cd-a3c2-4128-ae92-14c53cdb83c1 /media/BackupDisk           ext2    defaults        0       2
Then reboot and see if it's mounted. If yes, it should work. You can force a fscheck on reboot issuing:
> sudo shutdown -rF now
Let me know if you had success.

---

### Post by koenfloris on 2010-06-07
seems to have worked.. thx

but.. where does the 2 do? i know that 0 and 1 means. ( check or no-check ), but what does 2 do?

and i now have a ksudo in order to mount, but that is not a problem.

---

### Post by wieman01 on 2010-06-07
Hi, 

0 is no mount as you said, 1 for checking with 1st priority, usually reserved for the root partition, 2 stands for file-check after root (i.e. 1). Guess you could also chose 1 instead, but since it's a backup partition, 2 will do.

Want to get rid of the ksudo when mounting? Try this first:
> sudo chmod 777 /media/BackupDisk
> sudo chown your_username:your_username /media/BackupDisk
If this doesn't do the job, we'll try something else.

---

