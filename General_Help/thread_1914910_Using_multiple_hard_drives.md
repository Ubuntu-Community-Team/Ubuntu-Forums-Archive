---
title: "Using multiple hard drives"
date: 2012-01-25
forum: General Help
---

### Post by bigmug on 2012-01-25
OK so I'm completely new to ubuntu and linux. I just recently installed it to save myself from having to pay microsoft for their operating system.  So far I'm liking ubuntu very much. Looks and feels good.

Here's where I need help though. I don't really have a clue how to do this. I've spent about an hour googling it and reading things but I'm still a bit clueless.

My situation:

I have one solid state drive, which I have the operating system installed on. 

I also have a 1TB HDD that I want to use, for my other programs, photos, videos, music etc. The hard drive is completely empty. But I Have no idea how to set this up. Downloaded GParted, but have no idea what to do with it.

Please help.

---

### Post by stefangr1 on 2012-01-25
You open a terminal, and type
```
sudo fdisk -l
```

For each disk in your system, you should get something like
```
Disk /dev/sda: 2199.0 GB, 2199023255040 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```

One of them is your ssd, is has already some partitions listed. The other one is about 1000GB big and is your new drive. I now assume that /dev/sda is your ssd and /dev/sdb your 1000GB drive.

You then start Gparted, by typing
```
sudo gparted /dev/sdb
```

Note: if at this stage you see a list of partitions, something went wrong and you opened the wrong disk. Continuing may destroy all data on it, so be careful!

In the "Device" menu, you should choose "create new partition table". After that, you should press the "New" button to make some partitions. You should probably make it a primary partition, choose ext4, and enter a partition label.

After saving all changes, Ubuntu should automount the new disk.

---

### Post by bigmug on 2012-01-25
Thankyou, I've done exactly this. But how do I make sure things I save/download save on which drive?

---

### Post by stefangr1 on 2012-01-25
> **bigmug said:**
> Thankyou, I've done exactly this. But how do I make sure things I save/download save on which drive?

In your case, every directory will be on the ssd, except for the directory in which the 1000GB disk is mounted and all it's subdirectories.

Default locations are specific to the software you use, not to the operating system.

---

### Post by bigmug on 2012-01-25
I see... How do I move these directories to my HDD? I just want to be able to download and save things onto my HDD instead of it automatically going to my SSD. Because my SSD has very small capacity and I only intended to have the operating system and a few programs on it. Sorry i'm a complete noob

---

### Post by stefangr1 on 2012-01-25
> **bigmug said:**
> I see... How do I move these directories to my HDD? I just want to be able to download and save things onto my HDD instead of it automatically going to my SSD. Because my SSD has very small capacity and I only intended to have the operating system and a few programs on it. Sorry i'm a complete noob

If putting the files on the new disk manually isn't sufficient for you, you could consider puting your /home directory on it's own partition. while that's a relatively straightforward procedure during an install, doing it afterwards involves some understanding of the commandline and the system.

[Here is a tutorial]("https://help.ubuntu.com/community/Partitioning/Home/Moving") on how to move /home to it's own partition.

---

### Post by bigmug on 2012-01-25
Ah, thankyou, that's what I needed to know. I'll have a read of that. :)

---

### Post by jim_deadlock on 2012-01-25
An easier method would be to just mount your HDD inside your home folder.

```
sudo blkid
```

... will show your devices, make a note of the ID for your HDD.

```
gksudo gedit /etc/fstab
```

Find the line which shows your HDD and change the mount point, for example:

```
UUID=41dc5200-cb0e-4668-b601-fbc2114b40e2 /media/Maxtor ext4 defaults 0 2
```

... change to:

```
UUID=41dc5200-cb0e-4668-b601-fbc2114b40e2 /home/jim/HDD ext4 defaults 0 2
```

Save and reboot, then you'll see your HDD in your home folder and you can save stuff there, no need to mess about repartitioning your home folder.

---

### Post by oldfred on 2012-01-25
I mount two data partitions, one NTFS for sharing with XP which I now do not use much but still have Firefox & Thunderbird profiles in and a ext3 data partition for Linux data. I do this as I have multiple installs of Ubuntu on my system. I often suggest at least one install per hard drive so every drive is bootable in an emergency.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

