---
title: "[SOLVED] accidentally delete /etc/fstab.. what should i do?"
date: 2009-07-24
forum: General Help
---

### Post by Ajat on 2009-07-24
Hi i did a serious mistake.. I accidentally remove important file /etc/fstab..

now i can boot to my kubuntu..(i'm back to windows now)
is there a way i can recover this file..

please help.

---

### Post by Ajat on 2009-07-24
perhaps someone can guide me to create new fstab file..
here is the map of my partition

/dev/sda1  ntfs        (my windows vista partition)
/dev/sda2  extended
/dev/sda5  ntfs        (some data such as that movies,mp3,photos)
/dev/sda7  ext3         root
/dev/sda6  linux-swap


can someone formulate fstab for me. Thanks before.. 
(now i'm using this windows again after 32 days without it )

---

### Post by aysiu on 2009-07-24
> **Ajat said:**
> perhaps someone can guide me to create new fstab file..
here is the map of my partition

/dev/sda1  ntfs        (my windows vista partition)
/dev/sda2  extended
/dev/sda5  ntfs        (some data such as that movies,mp3,photos)
/dev/sda7  ext3         root
/dev/sda6  linux-swap


can someone formulate fstab for me. Thanks before.. 
(now i'm using this windows again after 32 days without it )
Yeah, the /etc/fstab file is just a text file. Using a live Kubuntu CD, mount your Kubuntu partition and using a special *kdesu*-launched Dolphin (or whatever the Kubuntu file manager is), create a text file with these contents: ```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

#/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
#/dev/sda5 /media/data ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda7 ext3 / ext3 relatime,errors=remount-ro 0 1
/dev/sda6 none swap sw 0 0
``` I put the two NTFS as commented out (inactive) with the *#* at the beginning of the line, because I don't know what the mount points are (I guessed /media/windows and /media/data, but it's up to you to figure out or create the directories.

You may also, once you get Kubuntu bootable again, want to use the *vol_id --uuid* command to get the UUIDs of the partitions instead of just their names. For example ```
sudo vol_id --uuid /dev/sda7
``` will tell you the UUID for /dev/sda7, and then you would use ```
UUID=*somelonggibberishthatcameoutofthelistcommand*
``` instead of ```
/dev/sda7
``` at the beginning of the line.

---

### Post by Ajat on 2009-07-24
Thanks aysiu.. you really save me.. now i'm posting this from my kubuntu..AND now i don't need to enter a password again everytime i play music from DATA. Cool.

instead of using the live CD, i boot from recovery menu, and run
```
sudo nano fstab
```
creating fstab in /root folder and then moved it to /etc

> **ysiu said:**
> 
/dev/sda7 ext3 / ext3 relatime,errors=remount-ro 0 1


due to the error message this line gave, i change this line to
```
 /dev/sda7  / ext3 relatime,errors=remount-ro 0 
```

best regards

ajat.

---

