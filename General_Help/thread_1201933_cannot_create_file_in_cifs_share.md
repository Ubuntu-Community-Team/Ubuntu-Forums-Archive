---
title: "cannot create file in cifs share"
date: 2009-07-01
forum: General Help
---

### Post by EnterTheDarkSide on 2009-07-01
hello,

i created a cifs share for my windows shared drive in ubuntu, but when i tried to create files in the share i'm getting a permission denied error. i created the shared like this:

sudo mount -t cifs //192.168.0.101/g share -o username=xxxx,password=xxxx,iocharset=utf8,file_mode=0777,
dir_mode=0777

could anybody tell me what i did wrong, thanks.

---

### Post by blueridgedog on 2009-07-01
The host computer that is sharing "g" or "g share" (not certain which, as I don't recall being able to use spaces in UNC share paths) may not have the permissions setup to allow you to create files.  If it is a windows system, you need to adjust the NTFS (local) permissions on the root folder (right click, properties etc) and the share permissions (again right click, then properties then sharing (I think)).

---

### Post by EnterTheDarkSide on 2009-07-01
hi, thanks for the reply.

"g" is actually the drive that is being shared on the windows system. "share" is the mount point on ubuntu. the user/pass im using to connect to that drive has full permission (i can write to the drive using the same user/pass on a different windows box).

---

### Post by blueridgedog on 2009-07-01
Then do you own "share" on the ubuntu box?  I would have expected a full path to the mount point, such as /home/USER/share.

---

### Post by EnterTheDarkSide on 2009-07-01
yes i do own "share". the full path to it is /mnt/share. but when i was entering the commands i was already in /mnt and therefore i could just enter "share" as the mount point.

the drive was mounted successfully. i could read but i just cannot write.

---

### Post by agathian on 2009-07-01
Did you try including "rw" in the options?

Also- may be if you post the output of "mount" commands, that will also help....

---

### Post by EnterTheDarkSide on 2009-07-01
i tried including the "rw" in the options but the result were the same. i got a permission denied error when i tried to create a file in the share.

sorry but i didn't understand what you meant by "post the output of mount". when i mounted it it was fine. the problem is when i tried to create (write) to the "share" that the permission denied error occurred.

---

### Post by agathian on 2009-07-06
> **EnterTheDarkSide said:**
> 
sorry but i didn't understand what you meant by "post the output of mount". when i mounted it it was fine. the problem is when i tried to create (write) to the "share" that the permission denied error occurred.

just type "mount" and press enter. that will display the current mount points, corresponding mount options/parameters, etc..

---

### Post by EnterTheDarkSide on 2009-07-08
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sdb1 on /mnt/rasengan type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /mnt/winxp type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
//192.168.0.101/g on /mnt/familycom-share type cifs (rw,mand)
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

the last line between the ">" and "<" is my cifs mount to a windows share. do you see any reason why i can't write to that share?

---

### Post by agathian on 2009-07-10
> **EnterTheDarkSide said:**
> 
the last line between the ">" and "<" is my cifs mount to a windows share. do you see any reason why i can't write to that share?

based on the mount permissions, No. 
 
Is the account you are using to map has write permission on those folders ?

Is the windows share created with full permissions? (dumb Q, i know)

can you also post the output of "ls -l" of the mountpoint?

---

### Post by EnterTheDarkSide on 2009-07-10
> **agathian said:**
> based on the mount permissions, No. 
 
> Is the account you are using to map has write permission on those folders ?
Yes the account i'm using to map the Windows share drive has full permission.

[QUOTE]Is the windows share created with full permissions? (dumb Q, i know)
Yes

> can you also post the output of "ls -l" of the mountpoint?
drwxrwxrwx 1 root root     0 1980-01-01 00:00 familycom-share

do you think it might have something to do with the smb.conf file. i read some where that you have modify that file.

---

### Post by EnterTheDarkSide on 2009-07-15
i finally figured out what was wrong. the syntax for the mount was correct, but the problem was that because the name i used to log into the windows share had space "firstname lastname", i needed to enclose the name in double quotes in the mount command: username="firstname lastname". after i did that i was able to write to the share.

---

