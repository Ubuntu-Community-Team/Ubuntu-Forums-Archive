---
title: "Storage device manager problem"
date: 2010-10-14
forum: General Help
---

### Post by nicki20048 on 2010-10-14
Hi, I have just upgraded to Ubuntu 10.10 but am still fairly new to Linux and Ubuntu.

I am having a problem in  setting permissions in the storage device manager, where I am having  difficulty in getting ownership of a file system . The screen shot below  shows my settings (as you can see the owner set to 1000):

[[IMG]http://media.use.com/images/s_4/ea0459175ad81d2276fa.jpg[/IMG]]("http://www.use.com/ea0459175ad81d2276fa")

But as you can see from the next screenshot I do not have ownership of the drive

[[IMG]http://media.use.com/images/s_4/a93be2d673bcdf90ecdb.jpg[/IMG]]("http://www.use.com/a93be2d673bcdf90ecdb")

If anybody has any ideas I would be grateful, maybe i'm missing something obvious.

---

### Post by dcstar on 2010-10-14
> **nicki20048 said:**
> Hi, I have just upgraded to Ubuntu 10.10 but am still fairly new to Linux and Ubuntu.

I am having a problem in  setting permissions in the storage device manager, where I am having  difficulty in getting ownership of a file system . The screen shot below  shows my settings (as you can see the owner set to 1000):
.........

You are not the "owner of the device", root is because the system is mounting the drive.

If this is an external drive then you should not be using this tool, it is for internal drives.

---

### Post by nicki20048 on 2010-10-14
It is an internal drive which has been partitioned (one partition has windows installed on it). I can access/edit all the files on my windows partition (sda2) but for whatever reason I can't with the other partition

---

### Post by nicki20048 on 2010-10-14
It is an internal drive which has been partitioned (one partition has windows installed on it). I can access/edit all the files on my windows partition (sda2) but for whatever reason I can't with the other partition

---

### Post by nicki20048 on 2010-10-15
bump

---

### Post by nothingspecial on 2010-10-15
Change the ownership of the drive from root to you

```
sudo chown -R nicola:nicola /path/to/drive
```

Change path to drive to the mountpoint of the drive eg

```
sudo chown -R nicola:nicola /media/disk
```

But bear in mind, it may be a file system that does not support linux file permissions, in which case you will have to edit fstab in order to set the permissions on mounting. Read this

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by nicki20048 on 2010-10-15
> **nothingspecial said:**
> Change the ownership of the drive from root to you

```
sudo chown -R nicola:nicola /path/to/drive
```

Change path to drive to the mountpoint of the drive eg

```
sudo chown -R nicola:nicola /media/disk
```

But bear in mind, it may be a file system that does not support linux file permissions, in which case you will have to edit fstab in order to set the permissions on mounting. Read this

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Thanks, gave that a try but this is what i'm getting:

[[IMG]http://media.use.com/images/s_4/9a616999b1d40973c1d5.jpg[/IMG]](http://www.use.com/9a616999b1d40973c1d5)

Also the drive is an FAT file system

---

### Post by nothingspecial on 2010-10-15
Ok, you will have to add an entry to fstab

First back up your fstab just incase I`m talking nonsense or you delete something by mistake.

```
sudo cp /etc/fstab /etc/fstab_bak
```Then you need to find the uid of the drive. 

```
sudo blkid
```Next, make a mountpoint
```

sudo mkdir /media/whatever_you_want_to_call_it
```

Then you need to edit fstab
```

gksudo gedit /etc/fstab
```Then add a line like this to the bottom
```

UUID=LOADS-OF-RANDOM-LETTERS-AND-NUMBERS    /media/whatever_you_called_it     vfat     uid=nicola,gid=nicola,utf8     0 0
```Then reboot

---

### Post by nicki20048 on 2010-11-02
> **nothingspecial said:**
> Ok, you will have to add an entry to fstab

First back up your fstab just incase I`m talking nonsense or you delete something by mistake.

```
sudo cp /etc/fstab /etc/fstab_bak
```Then you need to find the uid of the drive. 

```
sudo blkid
```Next, make a mountpoint
```

sudo mkdir /media/whatever_you_want_to_call_it
```Then you need to edit fstab
```

gksudo gedit /etc/fstab
```Then add a line like this to the bottom
```

UUID=LOADS-OF-RANDOM-LETTERS-AND-NUMBERS    /media/whatever_you_called_it     vfat     uid=nicola,gid=nicola,utf8     0 0
```Then reboot

Thanks, followed that exactly but i'm still not the owner of the drive :(

---

