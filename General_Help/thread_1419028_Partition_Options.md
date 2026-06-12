---
title: "Partition Options"
date: 2010-03-01
forum: General Help
---

### Post by tuxman7 on 2010-03-01
Hi, im new to the forums but i have had experience with linux in the past.

Here is my situation. 

I cleaned out my pc today and reinstalled windows. I basically plan to switch over to Ubuntu on a more permanent basis. I plan to use windows (7) for gaming and a few other things i can only run on windows.

Currently i have a 1Tb hdd (931GB cap) which has 879GB remaining after the windows install with all the programs i need on it.

I plan on installing ubuntu and giving it a generous 500 or 600GB parition. I have a backup of all my files and documents and i was wondering should i put them on the ubuntu parition or should i keep the ubuntu partition to 100GB or so and have another partition for the storage of the files?

The reason i mention this is because i heard that you shouldnt have files and docs on your root drive, but since i have a backup would it be ok for me to do this anyway?

Also if it comes to the point that i need extra space for windows and i have space in ubuntu, can i resize the partitions after the system is already up and running on dual boot?

thanks

---

### Post by rahilm on 2010-03-01
100 GB for ubuntu is actually more than sufficient. (I have a mere 160GB hard disk in which windows 7 and ubuntu are crammed in)
it is somewhat good that you have a seperate "/home" partition for storing your personal data. That helps when you want a common /home for many linux distros. or you have a habit of installing the latest ubuntu rather than waiting for the next LTS.

Basically a different /home partition will save your data and your configuration settings so that say, if you re-install ubuntu then firefox will continue working as it before, same bookmarks, configurations and maybe even some addons. It will also work when you install, say, fedora in another partition but will retain all the firefox properties.

A special note. I usually do not store data on any linux partition. Only the most private data goes there. because you cannot access those via windows.

---

### Post by tuxman7 on 2010-03-01
Ok, i see what you mean, but how should i got about that when installing ubuntu? As recall the option for the parition is basically if i create an unallocated space for ubuntu then another space for the home directory, how would i set the home directory to the other partition?

I think im starting to confuse myself, im sorry im used to keeping things simple - windows partition with games and apps, linux partition with all my work and data lol.

Putting something in the middle feels weird to me.

---

### Post by geirha on 2010-03-01
Just leave unallocated space for Ubuntu, then when you get to the partitioning part in the Ubuntu installer, choose Manual. From there:
1. Create an extended partition of all unallocated space.
2. Create a logical (i.e. inside the extended) partition and set / as mount-point.
3. Create another logical partition and set /home as mount-point
4. Create a swap partition. The size of it doesn't matter too much, but make it a little bit larger than your physical mem in case you want to hibernate.

---

### Post by tuxman7 on 2010-03-01
Ok, and i can do all that in the UI during installation? Sorry for asking, i just never really paid alot of attention to the other settings.

---

### Post by -kg- on 2010-03-01
> I plan on installing ubuntu and giving it a generous 500 or 600GB parition. I have a backup of all my files and documents and i was wondering should i put them on the ubuntu parition or should i keep the ubuntu partition to 100GB or so and have another partition for the storage of the files?

The reason i mention this is because i heard that you shouldnt have files and docs on your root drive, but since i have a backup would it be ok for me to do this anyway?


It sounds like you might want a separate /home partition.  When you install Ubuntu using one of the default installation schemes, it will create two partitions; a "/" (root) partition and a swap partition.  The /home directory will be contained on this root partition.  You can, however, create a separate "/home" partition.  This facilitates the upgrade process by preserving your files and data.

In order to create such a partition during the installation process, it will be necessary to use the Manual Partitioning partitioning method.  Using this method, it will be necessary to create all partitions manually during the installation.

You will need to create a root partition of, say, around 15 to 20 GB, depending on what you anticipate doing in Ubuntu.  Software packages, kernels, etc., will be stored there, as well as various other system-related directories and files.

You will need a swap file.  Usually suggested is around 1.5 X the amount of RAM in your system, though that is variable.

Then you will create one other partition...your /home partition.  This is the partition that you should create at 500 or 600 GB; whatever you anticipate you need.  I'd say that 500 GB is some plenty of storage! :P  You can make it whatever size you anticipate you will need.

I don't know what experience you have in hard drive partitioning.  You can get the basics by reading the documentation at the link in my signature block.  After creating your partitions, you must mark the mount point for each; "/" for the root partition and "/home" for the home partition.  The swap partition does not need to be marked; it will be recognized for what it is.

[This guide]("http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide") will show you basically the procedure using the Manual Partitioning option during the installation process.

---

### Post by tuxman7 on 2010-03-01
Ok that makes sense.

However, im confused about one more thing, you say 15/20GB for the root which holds the OS, system files, programs etc... what if im downloading lots of other programs from the repositories, are they going to go to the root or the home?

If the root then 15/20 seems a bit small to me, as i practised with a 200GB partition the other day and the root had 186GB after the install, im assuming this took into account the swap (4GB) but that would have meant the ubuntu install was 10GB(ish).

I just dont know what size to set the root at. If i need to would i be able to resize the root partition at a later date?

---

### Post by SaintDanBert on 2010-03-01
> **rahilm said:**
> 
...
A special note. I usually do not store data on any linux partition. Only the most private data goes there. because you cannot access those via windows.

Actually, you can access EXT2 and EXT3 file systems from Windows-XP
(I have not tried win-Vista or win-7.) using "Ext2 Installable File system for Windows" [http://www.fs-driver.org/](http://www.fs-driver.org/). I have used this for many years with minimal troubles.

Once installed, use the win-dose control panel and point IFSdrive at a compatible file system, name a drive letter, and use it read-write.
There are wrinkles so be certain that you read the docs.

~~~ Dan 0;-D

---

### Post by tuxman7 on 2010-03-01
I cant decide how much space to parition for the / dir as im planning on installing alot of apps and working with audio and video alot.

Also is it not risky to have a separate parition for the /home, im afraid of access issues arising from this type of partition scheme.

Any advice?

---

### Post by geirha on 2010-03-02
Go with 20 gig for /. Should be more than enough. The audio and video you'll be editing/creating will be saved under /home, so /home is where you need all the space. The programs themselves are stored on /, but will typically only be a few mebibytes in size.

Access issues are typically only a problem with external drives and "alien" filesystems like FAT32 and NTFS. Make both / and /home ext4 and you won't have any problems.

---

### Post by cd-r80 on 2010-03-02
I have:

/dev/sda5             4.6G  334M  4.1G   8% /
/dev/sda10            1.9G  935M  883M  52% /var
/dev/sda7             4.6G  139M  4.3G   4% /tmp
/dev/sda8              50G  4.3G   43G  10% /home
/dev/sda9             5.7G  2.8G  2.7G  52% /usr
y.

separate /tmp at least 4.6G for burning DVDs. 
separate /var . In the past my HD was filled with logs (attack). I had problems to boot / partition filled... Now I always put separate /var.
/swap double of your memory.
separate /usr for programs I have only 5.7G but I am using xubuntu with no effects, But quite a lot programs.

---

### Post by tuxman7 on 2010-03-06
sorry for late reply, i ended up giving a 4gb swap, 20gb / and 100gb /home :) working fine and i got to know gparted quite well over the last few days and i have a better unstanding of partitioning and hardware so i can easily update the space as i need it :)

thanks everyone for the info

---

