---
title: "Hard Disk mounting ?"
date: 2010-08-15
forum: General Help
---

### Post by binarylife on 2010-08-15
I know that when I need to access filesystem It'll mounted to the desktop ,
and I have another drive which is 50GB, and used between Windows 7 and ubuntu (NTFS FILE SYSTEM) , so whenever I need to access this drive it should be "mounted" but with my click ,so is there anyway which I can make this drive "mounted" at startup becauase i need it for some reasons ? 
Thanks :confused:

---

### Post by mhgsys on 2010-08-15
Yes you can ; 

I'm going to show you a example; **I'll use /dev/sdb1 as my example and bold out what info I mean'**
also; you should writeout/save the file you edited of course.

you should make a directory you want to mount to; 
```
sudo mkdir /media/stor
```
then you can mount your disk like;
```
sudo mount /dev/sdb1 /media/stor
```

when mounted; in your /etc/mtab you'll find some valuable data
f.e
```
nano /etc/mtab
``` gives 
>  /dev/sdb1 /media/stor fuseblk **rw,nosuid,nodev,allow_other,**blksize=4096 **0 0**

Were gonna use some of that data to put in fstab;
best way is to use **blkdid** so all disks have there own UUID.
use the command blkid to obtain these UUID; 
```
blkid
```

f;e blkid gives me;
> /dev/sda1: UUID="BC9003C9900388DA" TYPE="ntfs" 
/dev/sda2: UUID="8d824aa4-eb23-4333-b62b-7edf4d9b9135" TYPE="swap" 
/dev/sda3: UUID="a6bec86d-0211-4086-a239-9bafed817dc7" TYPE="ext4" 
**/dev/sdb1:** LABEL="STORAGE" **UUID="0CF0267DF0266CE0" TYPE="ntfs" **
/dev/sdc1: LABEL="DATA" UUID="561CFADD1CFAB759" TYPE="ntfs

Now; We wanted to have /dev/sdb1 mounted as /media/stor at boot; So were gonna edit the **/etc/fstab** and add the** UUID** and some **info we found** in **/etc/mtab.**
 
```
sudo nano /etc/fstab
```
and add the line
> UUID=0CF0267DF0266CE0 /media/stor         ntfs  rw,nosuid,nodev,allow_other     0       0



you can now test you're fstab by umounting the manual mount 
```
sudo umount /dev/sdb1
```
and mount by fstab ```
 sudo mount -a
```

after doing this; it will always mount on (re)boot

---

### Post by binarylife on 2010-08-15
Wow i apperciate your way and I gonna try it , but I wonder if there is a program or sth ready to do it thanks

---

