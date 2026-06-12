---
title: "How do i mount a partition automatically at startup"
date: 2009-11-30
forum: General Help
---

### Post by Jammanuser on 2009-11-30
Hi all.
I was wondering how to setup my Ubuntu, so it automatically mounts a particular partition at startup. A couple of my partitions it automatically mounts, but not all of them. ;)

Thanks in advance.

-Jam Man

:guitar:

---

### Post by akakingess on 2009-11-30
> **Jammanuser said:**
> Hi all.
I was wondering how to setup my Ubuntu, so it automatically mounts a particular partition at startup. A couple of my partitions it automatically mounts, but not all of them. ;)

Thanks in advance.

-Jam Man

:guitar:

Are the ones that automatically mount in your fstab file already, and if so, is the one not automounting in there as well or not listed? If you could post the output of your /etc/fstab, simply enter ```
sudo gedit /etc/fstab
```
enter your password and your current fstab file should come up within gedit, if you don't mind posting that info within some code tags so it's easier for us to read, that may help us figure out why some are mounting and some are not.  Also, is the one that is not automounting NTFS formatted where the others are not, and also I assume that you have already checked out [http://ubuntuforums.org/showthread.php?t=785263&highlight=automounting+drives+Ubuntu](http://ubuntuforums.org/showthread.php?t=785263&highlight=automounting+drives+Ubuntu) as I have found some of these tips and tutorials useful in the past..

---

### Post by Jammanuser on 2009-11-30
Yes, the ones that are mounted are in the /etc/fstab, and the ones that don't mount are not.
The truth is, I've already known about the /etc/fstab, I just don't know how to configure the file so the other partitions will be mounted too. :shame:
And no, I haven't read that thread yet. I'll do it now.

---

### Post by Jammanuser on 2009-11-30
Here is my fstab:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda2
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0

#/dev/sda6
UUID=162839AD28398D2D   /media/DATA    ntfs-3g   defaults      0    0

```

---

### Post by Jammanuser on 2009-11-30
EDIT: Sorry, duplicate post.

---

### Post by bodhi.zazen on 2009-11-30
So , add an entry for the partitions you wish to mount.

See :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

If you need assistance, please provide us with additional information. What partition are you trying to mount, where , and what file system (ext4, NTFS ??? )

---

### Post by snake_eyes on 2009-11-30
> sudo pico /root/.smbcredentials

# Add the following lines
username=winusername
password=winpassword

# change the permissions of the file so only root can read and edit it:
> sudo chmod 700 /root/.smbcredentials

# Now edit fstab:
> sudo pico /etc/fstab

# at the end of the file, insert one (1) of the following 3 lines according to your needs. Make sure you change "netbiosname" and "sharename" to the correct names for the server you are trying to connect to.

# For a password protected share with read/write permission.
//server/admin	/home/admin/server        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

# For a non-password protected share with read/write permission use this instead:
//server/admin	/home/admin/server        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

# For read only guest access:
//server/admin	/home/admin/server        cifs    guest,iocharset=utf8 0 0

# Reload fstab
> sudo mount -a

Cheers,

---

### Post by akakingess on 2009-11-30
Wow, sounds like we have made some progress and gotten reinforcements, so thank you all that have helped out and I may step out of the way as I am not the most experienced of the group, just trying to help where I can... Thanks again for all of the responses and hopefully we will get the OPs problem resolved in no time!

---

### Post by Jammanuser on 2009-11-30
```
gorilla@ubuntu:~$ sudo gedit /etc/fstab
[sudo] password for gorilla: 
gorilla@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-11-30 05:20 162839AD28398D2D -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-11-30 05:20 4EF4BF01F4BEE9FB -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-11-30 05:20 74D4CA25D4C9E986 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-11-30 05:20 786CF89A6CF853FA -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-11-30 05:20 dd4f326a-2165-40f6-aed4-2b44b15b71a5 -> ../../sda4
gorilla@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c5a8d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           34362       38185    30716280    7  HPFS/NTFS
/dev/sda2               6        1279    10233405    7  HPFS/NTFS
/dev/sda3           19765       34361   117250402+   f  W95 Ext'd (LBA)
/dev/sda4   *       17216       19764    20474842+  83  Linux
/dev/sda5           19765       20337     4602591   82  Linux swap / Solaris
/dev/sda6           20338       27986    61440561    7  HPFS/NTFS
/dev/sda7           27987       34361    51207156    7  HPFS/NTFS

Partition table entries are not in disk order
gorilla@ubuntu:~$ sudo gedit /etc/fstab


```
The partitions I want to mount is /dev/sda1 and /dev/sda2 and /dev/sda7.

---

### Post by Jammanuser on 2009-11-30
Thanks for the replies guysss. :)

---

### Post by akakingess on 2009-11-30
> **Jammanuser said:**
> Thanks for the replies guysss. :)

All of those partitions are NTFS so you need to make sure that you have some libs installed, I believe ntfs-config, and one other one that I can't think of off of the top of my head, but that should have been in the post that I referred to earlier.
Sorry, it may be NTFS-3G or something to that affect as well..

---

### Post by bodhi.zazen on 2009-11-30
List your partitions by UUID with :
```
sudo blkid
```

Then edit fstab with :

```
gksu gedit /etc/fstab
```

Put one entry for each partition you wish to auto mount

for example :

> # /dev/sda1[FONT=monospace]
[/FONT]UUID=copy_paste_UUID_for_sda1_here       /media/sda1       ntfs-3g         defaults      0   0

In that example I used "/media/sda1" as teh mount point, you may use any name you wish.

Make the mount point with :

```
sudo mkdir /media/sda1
```

and all should be good t ogo.

---

### Post by Jammanuser on 2009-11-30
Ok, thank you. :)
```
gorilla@ubuntu:~$ sudo blkid
[sudo] password for gorilla: 
/dev/sda4: UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" LABEL="Ubuntu-real" 
/dev/sda6: UUID="162839AD28398D2D" LABEL="DATA" TYPE="ntfs" 
/dev/sda7: UUID="786CF89A6CF853FA" LABEL="Programs" TYPE="ntfs" 
/dev/sda2: UUID="74D4CA25D4C9E986" LABEL="Recovery" TYPE="ntfs" 
/dev/sdb1: LABEL="SA-20G IPOD" UUID="3141-5926" TYPE="vfat" 
/dev/sda1: UUID="4EF4BF01F4BEE9FB" LABEL="WINXP-OS" TYPE="ntfs" 
gorilla@ubuntu:~$ sudo gedit /etc/fstab
^C
gorilla@ubuntu:~$ sudo gedit /etc/fstab
gorilla@ubuntu:~$ sudo mkdir /media/sda1
gorilla@ubuntu:~$ sudo mkdir /media/sda2
gorilla@ubuntu:~$ sudo mkdir /media/sda7
gorilla@ubuntu:~$ sudo gedit /etc/fstab

```

I did this, and here is the resulting file:
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0

# /dev/sda1
UUID=4EF4BF01F4BEE9FB     /media/sda1     ntfs-3g       defaults         0   0

# /dev/sda2
UUID=74D4CA25D4C9E986     /media/sda2    ntfs-3g        defaults         0   0

# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0

# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1

# /dev/sda5
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0

# /dev/sda6
UUID=162839AD28398D2D   /media/DATA    ntfs-3g   defaults      0    0

# /dev/sda7
UUID=786CF89A6CF853FA   /media/sda7   ntfs-3g    defaults      0    0

Hopefully this will work.

---

### Post by bodhi.zazen on 2009-11-30
Looks good. The only thing that may need to be modified is ownership and permissions ...

---

### Post by Jammanuser on 2009-11-30
> **bodhi.zazen said:**
> Looks good. The only thing that may need to be modified is ownership and permissions ...
And how do you modify those?

---

### Post by bodhi.zazen on 2009-11-30
In the 4th column, the options, where you have defaults, use uid= , gid = to assign user and group, you fmask and dmask for permissions.

users are identifed by number, enter the command :

```
id
``` to see info on your user, by default 1000

so ...

uid=1000,gid=1000,dmask=770,fmask=660

Unmount and remount the partitions

see the link on fstab I gave you for additional details.

---

### Post by akakingess on 2009-11-30
Just a side note, and not meaning to be a nuisance, but Jammanuser, when your issue is resolved, if you don't mind marking it as solved, then this will help others with the same issue as they will be able to find your post and all of the useful information within it and in turn may not have to start a new thread, I am just trying to help those that have issues that have not yet been addressed by allowing others to find your [SOLVED] post, and save room for others with issues.  Thank you for assisting with us trying to keep the forum as efficient as possible.  Thank you and please don't take this as me being a pain in the rear, just trying to help all of the others in the forums as well..

---

### Post by almufadado on 2009-11-30
Go to synaptics and search for +Storage +Device +Manager

Install Graphical Storage Device Manager

this works best for linux partitions

The mount option are all there 

Assuming you have them and use ntfs-3g, for ntfs partitions install :

"Enable/disable write support for any NTFS devices"

This program allow you to easily configure all of your NTFS devices
to allow write support via a friendly gui.
For that use, it will configure them to use the open source ntfs-3g
driver. You'll also be able to easily disable this feature.

For best results edit fstab (gksu gedit /etc/fstab) and replace the "/dev/sd?" by the partition UUID (UUID=<PARTITION ID HERE >

---

### Post by Jammanuser on 2009-12-01
Thank all of you. :)
My problem is now solved, and I'll be sure to mark the therad as solved.

Cheers.

-Jam Man

:guitar:

---

