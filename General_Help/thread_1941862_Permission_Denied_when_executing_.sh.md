---
title: "Permission Denied when executing .sh"
date: 2012-03-16
forum: General Help
---

### Post by Kilarin on 2012-03-16
Every time I start thinking I've gained some competency in the command line, I run into a brick wall that clearly points out what an ignorant newbie I am.

I've got a script that I run for backups.  I ran it just a month ago I think, and all was well.  BUT, now I try to run it again and I get the following:

don@m:/media/disk/mtools$ whoami
don
don@m:/media/disk/mtools$ groups
don adm dialout fax cdrom floppy tape audio dip video plugdev scanner netdev lpadmin admin fuse vboxusers truecrypt
don@m:/media/disk/mtools$ ls -l *.sh
-rwxrwx--- 1 don    don    2137 2012-03-07 16:05 long-bkp.sh
-rwxrwx--- 1 don    don     116 2009-03-10 21:43 test.sh
don@m:/media/disk/mtools$ ./long-bkp.sh
bash: ./long-bkp.sh: Permission denied

I've got the right user and group, and its clearly executable.  But I can't run the script.  I can't run any script in that folder anymore.   I checked the permissions up the chain:

drwxrwx---   1 don  don   4096 2012-03-16 07:47 mtools
drwxrwx---   1 don  don   8192 2011-10-30 20:41 disk
drwxr-xr-x  20 root root  4096 2012-03-16 07:59 media

disk and mtools are my owner and group.  media is root/root, but thats correct, isn't it?  home is root/root and I can still execute scripts from my home folder.

I used to be able to execute scripts from this folder, but now I cant.  What changed, and how do I fix it?

thanks!

---

### Post by codemaniac on 2012-03-16
Are you trying to run some admin commands from ./long-bkp.sh script , that requires admin privilege ?
Can you post the contents of the ./long-bkp.sh script ?

---

### Post by Kilarin on 2012-03-16
> Are you trying to run some admin commands from ./long-bkp.sh script , that requires admin privilege ?
Can you post the contents of the ./long-bkp.sh script ?
I thought perhaps that was the problem, and long-bkp.sh is kinda long and complex.  so I created a very simple script in the same folder.

-rwxrwx--- 1 don    don       6 2012-03-16 07:47 test2.sh
don@m:/media/disk/mtools$ cat test2.sh
ls -l
don@m:/media/disk/mtools$ ./test2.sh
bash: ./test2.sh: Permission denied

---

### Post by codemaniac on 2012-03-16
can you do the below .Just to check .
```
bash ./test2.sh
``` .

Your script permission to owner and group seems ok .All i am worried about is the execute permission of the shell itself .

```
ls -l /bin/bash
```

---

### Post by imachavel on 2012-03-16
what does gksu edit do? Doesn't it give you full permissions?

if it helps at all here is the return syntax for me when using those programs:

bash ./test2.sh
bash: ./test2.sh: No such file or directory
danel@danel-Dimension-4700:~$ ls -l /bin/bash
-rwxr-xr-x 1 root root 916692 2011-05-18 04:54 /bin/bash

---

### Post by Azdour on 2012-03-16
Hi,

I noticed the folder lives in /media. Is this a mounted HDD and has it mounted it with noexec? You should be able to type mount and see all your mounted drivers to check if this is the case.

---

### Post by imachavel on 2012-03-16
here is mine

mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/danel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=danel)
/dev/sr0 on /media/UDF Volume type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)

I wouldn't know what is under /media, is it a mounted drive? where is the media folder anyway? I wouldn't know but I've never heard of a drive in Linux being mounted under media. But what I have heard of is that it pops up once read by the mounted file system which is the operating system. Now is drive read by code which is in a folder such as /etc or /bin or what not, then the files load when the binary is read? Probably, but I don't think that the folder responsible for the drive is found in /media :lolflag:

I could be wrong, but /media is probably a folder that a certain type of video or image file format such as mpeg2 or jpeg or something or another is redirected to so that the user can interact with the program from the interface, if I'm wrong then shoot me :guitar:

---

### Post by jerome1232 on 2012-03-16
edit: Whoops, confused two posters.

---

### Post by Azdour on 2012-03-16
Hi,

Sorry, I was replying to the OP: Kilarin not you imachavel.

In the OP the path I see on the command line is:

```
/media/disk/mtools
```

So my advise was directed at Kilarin

---

### Post by wojox on 2012-03-16
What command did you use to mount this? Did you use "exec"?

```
sudo mount /media/disk/ -remount,exec
```

---

### Post by Kilarin on 2012-03-16
don@m:/media/disk/mtools$ bash ./test2.sh
total 34
-rwxrwx--- 1 don    don    2137 2012-03-07 16:05 long-bkp.sh
-rwxrwx--- 1 don    don       6 2012-03-16 07:47 test2.sh
-rwxrwx--- 1 don    don     125 2012-03-16 07:44 test.sh
don@m:/media/disk/mtools$ ./test2.sh
bash: ./test2.sh: Permission denied

THAT is fascinating! But I'm not entirely certain what it means.  permissions are wrong on bash?

don@m:/media/disk/mtools$ ls -l /bin/bash
-rwxr-xr-x 1 root root 916692 2011-05-18 04:54 /bin/bash


> I noticed the folder lives in /media. Is this a mounted HDD and has it mounted it with noexec? You should be able to type mount and see all your mounted drivers to check if this is the case.
yes, its a mounted HDD:


don@m:/media/disk/mtools$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /home/don/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=don)
/dev/sde1 on /media/expdrv type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
truecrypt on /tmp/.truecrypt_aux_mnt1 type fuse.truecrypt (rw,nosuid,nodev,allow_other)
/dev/mapper/truecrypt1 on /media/tc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by Azdour on 2012-03-16
Hi Kilarin:

> /dev/sdb1 on /media/disk type fuseblk (rw,**noexec**,nosuid,nodev,allow_other,blksize=4096,default_permissions)

It looks like /media/disk has been mounted with noexec and that's why I believe you cannot launch your script. 

I'm not familiar with fuseblk file systems. How do you mount that drive? Did you add an entry to /etc/fstab?

---

### Post by jerome1232 on 2012-03-16
> **Azdour said:**
> Hi Kilarin:



It looks like /media/disk has been mounted with noexec and that's why I believe you cannot launch your script. 

I'm not familiar with fuseblk file systems. How do you mount that drive? Did you add an entry to /etc/fstab?

I'm not sure if this is clear or not but fuseblk = ntfs

It would be nice to see your fstab, noexec isn't a default permission to my knowledge

```
cat /etc/fstab
```

---

### Post by Kilarin on 2012-03-16
[quote="wojox"]What command did you use to mount this? Did you use "exec"?[/quote]
[quote="Azdour"]I'm not familiar with fuseblk file systems. How do you mount that drive? Did you add an entry to /etc/fstab?[/quote]
This was once an 500gb external usb hard drive.  ntfs file system so I can use it when I boot into windows.
The power supply bit the dust, so I yanked the drive out of the case and mounted it internally.  Works fine that way.  Or at least it has for several years, until now. :)

it mounts automatically on boot and this is the fstab entry:

# Entry for internaly remounted 500gp usb drive /media/disk
UUID=C6A430F8A430ED15                      /media/disk    ntfs-3g      defaults,umask=007,user,uid=1000,gid=1000,locale=en_US.UTF-8,nobootwait  0  0

---

### Post by jerome1232 on 2012-03-16
> **Kilarin said:**
> This was once an 500gb external usb hard drive.  ntfs file system so I can use it when I boot into windows.
The power supply bit the dust, so I yanked the drive out of the case and mounted it internally.  Works fine that way.  Or at least it has for several years, until now. :)

it mounts automatically on boot and this is the fstab entry:

# Entry for internaly remounted 500gp usb drive /media/disk
UUID=C6A430F8A430ED15                      /media/disk    ntfs-3g      defaults,umask=007,[COLOR="Red"]user[/COLOR],uid=1000,gid=1000,locale=en_US.UTF-8,nobootwait  0  0

user implies noexec, just add exec in there somewhere and you should be golden

```
# Entry for internaly remounted 500gp usb drive /media/disk
UUID=C6A430F8A430ED15                      /media/disk    ntfs-3g      defaults,umask=007,[COLOR="Red"]user[/COLOR],[COLOR="Blue"]exec[/COLOR],uid=1000,gid=1000,locale=en_US.UTF-8,nobootwait  0  0
```

---

### Post by Kilarin on 2012-03-16
[quote="jerome1232"]user implies noexec, just add exec in there somewhere and you should be golden[/quote]

That fixed it!  Thank you very much everyone!

I added that "user" when I finally got around to upgrading to Ubuntu 11.10 and had a problem with my ntfs drives not mounting (which turned out to be the chkdsk flag)

I really appreciate the help folks!

---

