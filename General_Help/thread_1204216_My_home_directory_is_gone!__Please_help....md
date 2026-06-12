---
title: "My /home directory is gone!  Please help..."
date: 2009-07-04
forum: General Help
---

### Post by Ifaistos on 2009-07-04
Hello :-)

I am writing through my Windows machine :(
I turned off my machine and after a few hours I booted it.  It performed a "routine check" and although it was ok, then it produced various errors :

[B]* Checking file systems...
1080
fsck 1.41.3 (12-Oct-2008 )
/dev/sda2: clean, 30540/22839296 files, 14277418/45654721 blocks
Failed to open the device 'UUID=c9ae54a0-69e0-4939-9960-24347efb0eb5' : No such file or directory

fsck died with exit status 8

* File system check failed.
A log is being saved in /var/log/fsck/checkfs it that location is writable.
Please repair the file system manually
* A maintenance shell will not be started.
CONTROL-D will terminate this shell and resume system boot.
bash : no job control in this shell
root@.......:~#[/B]

This error message was happening in the past, but I was passing through that by typing "exit" and it continued rebooting and everything worked fine!

Right now I can't type anything!!  When I tried to type, it produced shapes like diamonds.  I changed keyboards but when I try to type "exit", I always get diamonds!!  So I press Alt-Ctrl-Del and it continues booting...

When I go to the login screen I give my username and password and I immediately get the error :

**Your home directory is listed as: '/home/evans' but it does not appears to exist.  Do you want to log in with the /(root) directory as your home directory?  It is unlikely anything will work unless you use a failsafe session.**

If I press yes, nothing works :(
If I choose a failsafe session nothing works either.

I really don't know what is wrong.  I use 8.10.
I would like to try typing "exit" and see what happens.  But I can't!!  

Any suggestions would be greatly appreciated.
This machine is my main one, where I have my e-mails, password managers, docs and all the data that I need...

Please help

---

### Post by tgalati4 on 2009-07-04
Boot with the Live CD.  Mount the disk.  Explore the file system and see if the home directory is still there.

While running from the Live CD, unmount the hard disk, open a terminal and run fsck:

Probably:

fsck /dev/sda2

and see what happens.

---

### Post by Ifaistos on 2009-07-04
I booted with a Live CD 8.10.
Gparted didn't have any problem identifying the partitions.

I run

sudo fsck /dev/sda2
and got the following result :
[B]fsck 1.41.3
e2fsck 1.41.3
/dev/sda2: clean, 30540/22839296, 14277418/45654721 blocks
[/B]

But I didn't unmount it first... how would I do that?

Thanks

edit : It was unmounted...
When I tried to run
sudo mount /dev/sda2 I got :
**mount : can't find /dev/sda2 in /etc/fstab or /etc/mtab**

Then I : sudo gedit /etc/fstab and the contents are :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db222afc-9936-45c2-bb33-7807c8871c5e /               reiserfs notail,relatime 0       1
# /dev/sda2
UUID=c823defe-c2e5-4e64-aadb-074d75059ffc /home           ext3    relatime        0       2
# /dev/sdc1
UUID=c9ae54a0-69e0-4939-9960-24347efb0eb5 /media/sdc1     reiserfs relatime        0       2
# /dev/sdb1
UUID=EACCD32ECCD2F433 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=13fccc89-1c14-433b-b96c-239a759c3b61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by michy99 on 2009-07-04
What do you get for```
sudo fdisk -l
```

---

### Post by Ifaistos on 2009-07-04
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005db12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056   83  Linux
/dev/sda2            7296       30030   182618887+  83  Linux
/dev/sda3           30031       30401     2980057+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34344e31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e447c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1

---

### Post by michy99 on 2009-07-04
Try replacing the UUID with /dev/sda2 in fstab and see if it mounts. If so, then the UUID may have changed and you will have to find out the new one.

Replace```
UUID=c823defe-c2e5-4e64-aadb-074d75059ffc /home ext3 relatime 0 2
```with```
/dev/sda2 /home ext3 relatime 0 2
```

---

### Post by philinux on 2009-07-04
michy is correct. Compare the uuid's from

cat /etc/fstab

to 

sudo blkid

---

### Post by Ifaistos on 2009-07-04
ubuntu@ubuntu:~$ sudo blkid
**/dev/sda2: UUID="c823defe-c2e5-4e64-aadb-074d75059ffc" SEC_TYPE="ext2" **TYPE="ext3" 
/dev/sda1: UUID="db222afc-9936-45c2-bb33-7807c8871c5e" TYPE="reiserfs" 
/dev/sda3: UUID="13fccc89-1c14-433b-b96c-239a759c3b61" TYPE="swap" 
/dev/sdb1: UUID="EACCD32ECCD2F433" LABEL="400 GB" TYPE="ntfs" 
/dev/sdc1: LABEL="Movie Editor" UUID="29f0dfc6-617a-4e9c-aa59-551a0b78e6d5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdf1: LABEL="RALLY2" UUID="765D-22C6" TYPE="vfat" 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db222afc-9936-45c2-bb33-7807c8871c5e /               reiserfs notail,relatime 0       1
# /dev/sda2
**UUID=c823defe-c2e5-4e64-aadb-074d75059ffc** /home           ext3    relatime        0       2
# /dev/sdc1
UUID=c9ae54a0-69e0-4939-9960-24347efb0eb5 /media/sdc1     reiserfs relatime        0       2
# /dev/sdb1
UUID=EACCD32ECCD2F433 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=13fccc89-1c14-433b-b96c-239a759c3b61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by michy99 on 2009-07-04
Run this and see if you get the same UUID.```
sudo blkid -c /dev/null /dev/sda2
```

---

### Post by Ifaistos on 2009-07-04
ubuntu@ubuntu:~$ sudo blkid -c /dev/null /dev/sda2
/dev/sda2: UUID="c823defe-c2e5-4e64-aadb-074d75059ffc" TYPE="ext3"

---

### Post by Ifaistos on 2009-07-04
Maybe the title of the thread is misleading.

Maybe there is nothing wrong with that... the problem could be in the fact that I can't type "exit"?

---

### Post by michy99 on 2009-07-04
Did you try replacing the UUID with /dev/sda2 in fstab and then```
sudo mount /dev/sda2
```

---

### Post by tgalati4 on 2009-07-04
It appears that you have your /home on a separate partition.  Many folks recommend doing this if you like to try a lot of distros so you don't have a /home on each distro that you test.  It's generally a good idea--provided--that you know what you are doing.    Are any of these disk drives external USB drives?

To mount a drive with the Live CD, you normally just double-click it on the Desktop--provided it shows up on the desktop.  To unmount it, Right-Click on the drive and select unmount.

It looks like your sda2 (/home) partition is OK, but your UUID in your fstab is messed up somehow.  You should be able to recover.

What did you do that would cause this?

---

### Post by Ifaistos on 2009-07-04
Thank you for your suggestions.

michy, I tried that but nothing happened.  I still get exactly the same error messages that I describe on my initial post.

tgalati, earlier today there was a power failure of several hours.  When I came back my UPS was still working and I turned off my Linux Machine properly.  I don't know what it would have caused this.

I am downloading as we speak the Desktop version of 9.04.  I have that on my netbook, and I think it's time I get it on my desktop as well.

I will format the root drive and leave the /home partition untouched.  I don't think there is any problem with it.  I used the LiveCD and backed some of the things up from the /home directory.

Only problem is I couldn't backup some files because I didn't have permission.  Another think that I am not sure how to do, is to convert the ext3 into ext4 for my home directory.

In general I think that this would solve the problem.  I have done the same thing from 8.04 to 8.10.

Let's hope I don't loose my /home directory.

---

### Post by Ifaistos on 2009-07-04
9.04 installation was very smooth.
No problems... nothing lost :-)

Thank you all for the help.

---

