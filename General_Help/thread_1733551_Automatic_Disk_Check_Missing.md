---
title: "Automatic Disk Check Missing"
date: 2011-04-19
forum: General Help
---

### Post by birkopf on 2011-04-19
Ubuntu has got this build-in check for errors which starts every 30 startups (if I remember well ) but my one gone missing... 

Strange. How can I turn it back on ?

I found in the forum some information about Bonager, but is this original automatic disk check software shipped with Ubuntu or another piece of software ?

---

### Post by dcstar on 2011-04-20
> **birkopf said:**
> Ubuntu has got this build-in check for errors which starts every 30 startups (if I remember well ) but my one gone missing... 


**Filesystems** have the startup check - this is firstly set in the /etc/fstab file to do a check and then each individual EXT filesystem has a setting to do a check every N mounts or n time period. The default is every 30 mounts.

---

### Post by birkopf on 2011-04-20
> **dcstar said:**
> **Filesystems** have the startup check - this is firstly set in the /etc/fstab file to do a check and then each individual EXT filesystem has a setting to do a check every N mounts or n time period. The default is every 30 mounts.

I suspected so. Recently I had to make changes to my FSTAB so I might removed something by mistake. I am including myfstab below because I cannot find option to do check every 30 mounts...

> 
# <file system> <mount point>  <type>  <options>  <dump>    <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda3 during installation
UUID=974c48a8-[***ermoved***]    /               ext4    errors=remount-ro 0       1

# /home was on /dev/sda4 during installation
UUID=8e72fcfd-[***ermoved***]    /home           ext4    defaults        0       2

# swap was on /dev/sda2 during installation
UUID=af00fa7b-[***ermoved***]    none            swap    sw              0       0

# vmware do mnt dodany przezemnie
UUID=9dde6ba5-[***ermoved***]    /mnt/vmware     ext4    defaults        0       0


---

### Post by tredegar on 2011-04-20
File system checking is set with **tune2fs** (works for ext3 and 4 as well) not **/etc/fstab**

Plese see **man tune2fs** for all the different options (check by interval, check by number of times mounted etc).

---

### Post by birkopf on 2011-04-20
> **tredegar said:**
> File system checking is set with **tune2fs** (works for ext3 and 4 as well) not **/etc/fstab**

Plese see **man tune2fs** for all the different options (check by interval, check by number of times mounted etc).

Ok. I used tune2fs to change automatic checkups to 20 by 
"sudo tune2fs -c 20 /dev/sdaXX" on all three of my partitions.

I will see if it works after 20 boots :)

---

### Post by tredegar on 2011-04-20
Why wait for 20 boots (might take years)?

Set it for two, test it, then set it for whatever you like.

---

