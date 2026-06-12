---
title: "USB drive read onyl file system"
date: 2010-04-25
forum: General Help
---

### Post by axakal on 2010-04-25
Hello,

I have a problem with my USB drive. When i try to make a file transfer, i get the error message which says that it is a 'read only file system' and i can not transfer any files. While looking for a way to solve the problem, i came across another case similar to what i have now which discussed in this thread:  [http://ubuntuforums.org/showthread.php?t=1382173](http://ubuntuforums.org/showthread.php?t=1382173) 

However, i didn't understand how to resolve the problem from that thread. 

Does anyone know how to fix the problem? 

Regards

---

### Post by prodigy_ on 2010-04-25
Start with ```
cat /etc/fstab
``` to see which partitions are auto-mounted at startup and with ```
cat /etc/mtab
``` to see which ones are currently mounted (and how).

---

### Post by axakal on 2010-04-25
Can you check those out?

These are the responses to the codes:
The first one:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=be45b4d4-7875-4935-b5cc-11167f1ce139 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=e5e9de98-c9df-4b4c-b4d2-35f30035979a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


The second one:

/dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-18-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/cem/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=cem 0 0
/dev/sdb1 /media/My\040Passport vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

---

### Post by prodigy_ on 2010-04-25
Alright. First of all you need to create a mount point and ensure it doesn't limit permissions for the mounted filesystem. For example:
```
sudo mkdir /media/ExternalDrive
sudo chmod -R 777 /media/ExternalDrive
```

Then you need to unmount your external drive (/dev/sdb1)...
```
sudo umount /dev/sdb1
```

...and mount it to the new mount point with appropriate options. For example:
```
sudo mount /dev/sdb1 /media/ExternalDrive -t vfat -o rw,nosuid,nodev,uid=$(id -u),utf8
```

If everything else is alright, you'll get write access to the partition after that.

Keep in mind, that this will have only temporary effect. To make changes permanent, you'll need to edit /etc/fstab. There's [a good HOWTO](http://ubuntuforums.org/showthread.php?t=283131) for that.

---

### Post by axakal on 2010-04-25
Thank you very much for your help. I will try your instructions. 

But i have a question though. While i try to unmount and mount it again is there are risk that i lose the information on USB drive or not? I mean will that operation format the drive?

---

### Post by dcstar on 2010-04-26
> **axakal said:**
> Thank you very much for your help. I will try your instructions. 


You shouldn't.

External drives are supposed to be managed by the system, not by people mucking around with system folders like /media - that folder is for the **sole **use of the system to use for removable media.

Plug the drive in as normal, start up gparted and find the drive/partition.

Use gparted to unmount it and then use the "check" function to do a fsck on the drive.

When completed, pull out the plug and then plug it back in and see if things have changed.

---

### Post by axakal on 2010-04-26
dcstar, thanks for your reply. I tried to unmount the USB drive from gparted as you said. However after when i try to 'check' it, an error occured. I saved the error message and it says: 

GParted 0.4.3

Libparted 1.8.8
Check and repair file system (fat32) on /dev/sdb1  00:07:00    ( ERROR )
     	
calibrate /dev/sdb1  00:00:01    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 625137344
size: 625137282 (298.09 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:06:40    ( SUCCESS )
     	
dosfsck -a -w -v /dev/sdb1



So i couldn't manage to check the drive.
Can you please advise me what to do after this point?

---

