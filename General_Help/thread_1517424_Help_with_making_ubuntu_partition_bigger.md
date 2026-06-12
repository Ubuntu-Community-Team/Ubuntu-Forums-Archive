---
title: "Help with making ubuntu partition bigger"
date: 2010-06-25
forum: General Help
---

### Post by antonvrg on 2010-06-25
hi there,

i made my ubuntu partition 10gb using wubi. i have an 80gb hard drive and want to make my ubuntu partition 40gb. is there a way i can do this without losing all my files and applications and other stuff like that?

thanks

-Anton

---

### Post by VH-BIL on 2010-06-25
There is, but I would advise backing up important data first. Check out this tutorial:
[*_Modify Your Partitions With GParted Without Losing Data_*]("http://www.howtoforge.com/partitioning_with_gparted")

---

### Post by antonvrg on 2010-06-25
> **VH-BIL said:**
> There is, but I would advise backing up important data first. Check out this tutorial:
[*_Modify Your Partitions With GParted Without Losing Data_*]("http://www.howtoforge.com/partitioning_with_gparted")


what i backup? i dont really want to lose all software and stuff... just got system set up. also where do i find the files/folders to backup?


-Anton

---

### Post by bcbc on 2010-06-25
If you installed with wubi, your partition is actually a file (\ubuntu\disks\root.disk) under your windows file system. There are some ways to increase it (see the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?"))...

however, if you're planning such a large ubuntu install, you really should consider installing direct to partition. Wubi isn't really intended for long term use and eventually you're going to have to do this.

---

### Post by antonvrg on 2010-06-25
> **bcbc said:**
> If you installed with wubi, your partition is actually a file (\ubuntu\disks\root.disk) under your windows file system. There are some ways to increase it (see the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?"))...

however, if you're planning such a large ubuntu install, you really should consider installing direct to partition. Wubi isn't really intended for long term use and eventually you're going to have to do this.

advice?

---

### Post by realzippy on 2010-06-25
Gparted will not help since you have to enlarge the windows folder first in which
ubuntu is installed.Have a look at the WUBI WIKI:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

BTW,would suggest a "real" installation (dualboot) of ubuntu...

---

### Post by realzippy on 2010-06-25
*advice?*

Insert the ubuntuliveCD and install it shrinking the existing windows partition(s)....
Good idea is to defragment windows before;maybe more than once..

---

### Post by antonvrg on 2010-06-25
ok i'll install usuing the dual boot. but can i keep what i have got with the .disk file. how do i use the . disk file when reinstalling/Re-Partitioning?

---

### Post by VH-BIL on 2010-06-25
running off a file in windows would be slower as well. To create a proper install of ubuntu you should delete the file version (to create free space if you need it) defrag you windows hard drive then use a partition tool to reduce the size of your windows partition. When you install Ubuntu you can create the relevant partitions in the free space.

---

### Post by antonvrg on 2010-06-25
> **VH-BIL said:**
> running off a file in windows would be slower as well. To create a proper install of ubuntu you should delete the file version (to create free space if you need it) defrag you windows hard drive then use a partition tool to reduce the size of your windows partition. When you install Ubuntu you can create the relevant partitions in the free space.

ok but can i keep what i've already set-up using the wubi crap?

---

### Post by realzippy on 2010-06-25
...what do you want to "save"?Personal data can be burnt to CD for example.
A list o installed packages can be ex/imported from synaptic...

Maybe fresh install is faster than backing up,especially if you do not not what to do...

---

### Post by VH-BIL on 2010-06-25
I do not know much about wubi, sorry. You might have to back your up data, then put it on your new install. Your applications should reinstall easily with synaptic.

---

### Post by bcbc on 2010-06-25
> **antonvrg said:**
> advice?

I'd partition my drive and migrate the wubi install to it. 

But it depends on how much space you have available on your drive and your comfort level. Some people would just do a fresh install, reinstall the same packages, and copy over the /home from your root.disk (which you can mount and view from either a live CD or another ubuntu install).

Whatever you do, buy an external and backup your data first (if you haven't already).

---

### Post by bcbc on 2010-06-25
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

See the above for advice on partitioning your drive

---

### Post by VH-BIL on 2010-06-25
> **bcbc said:**
> I'd partition my drive and migrate the wubi install to it. 

But it depends on how much space you have available on your drive and your comfort level. Some people would just do a fresh install, reinstall the same packages, and copy over the /home from your root.disk (which you can mount and view from either a live CD or another ubuntu install).

Whatever you do, buy an external and backup your data first (if you haven't already).

Do you migrate by using "dd" to move data from one device to another?

---

### Post by bcbc on 2010-06-25
> **antonvrg said:**
> ok i'll install usuing the dual boot. but can i keep what i have got with the .disk file. how do i use the . disk file when reinstalling/Re-Partitioning?

There is a shell script that will migrate a wubi install to a fresh partition. It doesn't work so well since some of the commands are no longer supported and it assumes grub-legacy is installed. There is a [bug]("https://bugs.launchpad.net/wubi/+bug/456549") registered for it. I've posted a modified script that works for me - tested on 9.10 and 10.04 fresh wubi installs.

You still have to do all the partitioning work beforehand. Anyway - depending on your **tolerance for risk** (and assuming you did backup), you could use this.

---

### Post by bcbc on 2010-06-25
> **VH-BIL said:**
> Do you migrate by using "dd" to move data from one device to another?

no, rsync.

---

### Post by antonvrg on 2010-06-25
i havn't used synaptic, i used ubuntu software center. can i export installed packages in that?

---

### Post by VH-BIL on 2010-06-25
Is your internet OK? just take a not of the installed applications then reinstall in Synaptic Package Manager or Ubuntu Software Center. It shouldn't take to long on a decent ADSL connection.

---

### Post by antonvrg on 2010-06-25
> **VH-BIL said:**
> Is your internet OK? just take a not of the installed applications then reinstall in Synaptic Package Manager or Ubuntu Software Center. It shouldn't take to long on a decent ADSL connection.

yeah but i got like 300 applications... (im looking for an easy way out)

---

### Post by VH-BIL on 2010-06-25
I would still reinstall using synaptic lol, but if you want to backup your installed applications check out [*_HOWTO: Backup all installed programs/packages_*]("http://ubuntuforums.org/showthread.php?t=819396")

---

### Post by antonvrg on 2010-06-25
ok thanks for ya help. should have sytem done right in a lazy few days.

---

### Post by VH-BIL on 2010-06-25
How many is a lazy few lol

---

### Post by oldfred on 2010-06-25
You can make a list of the installed packages with this:

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
You can regenerate new sources file
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)


 dpkg --get-selections > ubuntu-files

Then reinstall:
# must have saved ubuntu-files from previous install to this directory
dpkg --set-selections < ubuntu-files
apt-get -y update
apt-get dselect-upgrade

You can backup your /home and reinstall and all your user settings will be preserved.

[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

