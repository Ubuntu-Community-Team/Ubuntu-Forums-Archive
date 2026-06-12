---
title: "Help me with Gparted?"
date: 2011-04-07
forum: General Help
---

### Post by Bluestars on 2011-04-07
So I used the webui in windows to install a second partiton on my hd for Ubuntu.  In the webui it let me select the ntfs partiton and only make it 3 gb.  I figured I would later on be able to easily increase the size.

In Gparted it tells me that I have 2 partitons.  One with 147.34 Gb unused, and one with 371 Gb unused.  When I boot into Ubuntu however it tells me my home folder only has 500 mb left.  Im pretty confused.  

From looking at Gparted I should have a bunch of free space.  Why is telling me I'm almost out?

Attached is a screenshot of my Gparted so that someone can easily instruct me what to do.  Thanks guise.

---

### Post by ajgreeny on 2011-04-07
I am a bit lost!

What partitions did you have before you started playing around with them, and what did you want to end up with exactly?  The problem is that there is no linux operating system partition on the disk, just two swap partitions.  You also have two ntfs partitions, sda1 which is 507GB with almost 360GB used, and another, sda5 which is 384GB with only 12.7GB used.

Where do you think you put Ubuntu?  I hope you did not try to install ubuntu on an ntfs partition, as that is impossible.

Can you tell us a lot more about what you did, why you did it, and what you want to achieve.

---

### Post by aktiwers on 2011-04-07
What is your output of:
```
df -h
```

---

### Post by Bluestars on 2011-04-07
Originally I had ubuntu 10.04 booting next to Win 7.  I wiped the ubuntu partition, and I guess formatted it to NTFS.  I didnt have any blank dvds so I used Webui to try and install ubuntu 10.10 to the ntfs partition.  

My goal was to be able to dual boot win 7, and Ubuntu 10.10.  I'm pretty sure I the whole thing.

output of df -h


```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            3.9G  1.3G  2.4G  36% /
none                  4.0G  228K  4.0G   1% /dev
none                  4.0G  388K  4.0G   1% /dev/shm
none                  4.0G  100K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
/dev/sda5             385G   13G  373G   4% /host
/dev/loop1            3.9G  3.7G  1.2M 100% /home
/dev/loop2            3.9G  2.5G  1.2G  68% /usr
/dev/sda1             508G  360G  148G  71% /media/05BEB22D0F7B5B73
```

---

### Post by aktiwers on 2011-04-07
If I understand you correctly, you wanted the 508gb partition to be your /home partition?

Its not right now. Right now your home is on a small 3.9gb partition. I have not seen those /dev/loop drives before..  how did you install Ubuntu? Using Wubi or something like that?

Do you want to use the 508gb partition as home instead?

---

### Post by Bluestars on 2011-04-07
> **aktiwers said:**
> If I understand you correctly, you wanted the 508gb partition to be your /home partition?

Its not right now. Right now your home is on a small 3.9gb partition. I have not seen those /dev/loop drives before..  how did you install Ubuntu? Using Wubi or something like that?

Do you want to use the 508gb partition as home instead?


Yes, I would like to use the 500 gig one as the ubuntu/home one.  If that drive doesnt contain windows. 
 They are telling me in IRC webui is mainly used for evaluation, and that I should do a full install.  I don't want to lose my Windows partition though.

and yep installed via webui through windows 7.

---

### Post by aktiwers on 2011-04-07
Looking at your screenshot..  why do you have 2 swap drives?
One on 16gb and another on 22gb? :O

Usually One swap drive with 1gb is more than enough

---

### Post by ajgreeny on 2011-04-07
I assume the **df -h** output was from a live CD/USB?  It must have been as you do not have a ubuntu OS partition at all at the moment, unless you installed with wubi, which is something I can not help you with any more.

---

### Post by Bluestars on 2011-04-07
> **aktiwers said:**
> Looking at your screenshot..  why do you have 2 swap drives?
One on 16gb and another on 22gb? :O

Usually One swap drive with 1gb is more than enough

I really have no idea.

---

### Post by Bluestars on 2011-04-07
> **ajgreeny said:**
> I assume the **df -h** output was from a live CD/USB?  It must have been as you do not have a ubuntu OS partition at all at the moment, unless you installed with wubi, which is something I can not help you with any more.

No I ran df -h from my ubuntu install.  I did use webui to install linux.  Perhaps I should delete all of my partitons (including windows) and do a full install of ubuntu?

I use windows for games, and various things i cant get to work in ubuntu.  If I run windows through VMware inside of Ubuntu to play games, would I get the same effect as playing just on windows?  Have 8 gigs of ram and core2 quad.
If so I will just do away with windows and use it through a VM.

---

### Post by aktiwers on 2011-04-07
It looks like your partition setup is pretty messed up.

First you need to find out what drive is your Windows Drive. Either try browse through the files on the drives through Ubuntu or boot to Windows and look at the size of your C:\ drive.


 Im pretty sure that the 508gb disk is your windows though.
 
When you know this, I would recomment doint a clean install.
When the installer hits the partitioning menu, pick Manual Partioning.

Now delete alle partitions that are NOT your Windows Partition(all data will be LOST on those partitions). [COLOR=Red]So remember to backup if you have stuff you dont want to loose![/COLOR]
  After this you have 1 NTFS partition (your windows Partition) and a big chunk of empty space.


 
First create a 1gb SWAP partition.
Next create a 30gb EXT4 partition and in mountpoint type:
```
/
```
 Next create EXT4 partion on the remaining space, and in mountpoint type:  
 ```
/home
```
 You have now created a 1 gb Swap partiton (its like the page file in windows, used instead of RAM when needed). You have a system disk / on 30gb, for Ubuntu and the rest of the space is your /home partiton.
 

 Thats what I would do.

Edit:
Sadly you cant play 3D heavy games in VMware. It runs of a virtual video card and it cant performe 3D as well as your real video card

---

### Post by ajgreeny on 2011-04-07
> **aktiwers said:**
> It looks like your partition setup is pretty messed up.

First you need to find out what drive is your Windows Drive. Either try browse through the files on the drives through Ubuntu or boot to Windows and look at the size of your C:\ drive.


 Im pretty sure that the 508gb disk is your windows though.
 
When you know this, I would recomment doint a clean install.
When the installer hits the partitioning menu, pick Manual Partioning.

Now delete alle partitions that are NOT your Windows Partition(all data will be LOST on those partitions). [COLOR=Red]So remember to backup if you have stuff you dont want to loose![/COLOR]
  After this you have 1 NTFS partition (your windows Partition) and a big chunk of empty space.


 
First create a 1gb SWAP partition.
Next create a 30gb EXT4 partition and in mountpoint type:
```
/
``` Next create EXT4 partion on the remaining space, and in mountpoint type:  
 ```
/home
``` You have now created a 1 gb Swap partiton (its like the page file in windows, used instead of RAM when needed). You have a system disk / on 30gb, for Ubuntu and the rest of the space is your /home partiton.
 

 Thats what I would do.
+1

I agree with aktiwers!  Your partition arrangement is a mess at the moment, and a clean install to separate partitions will make things a lot better for you.

And you are right, wubi, (not webui, hence the confusion) is only really for evaluation purposes, and was never meant to be a way to install a dual boot system for long term use.

If you want any more help with the install, have a look at the site I link to below for installing with a separate home partition.  Even though this is not for a dual boot arrangement, it should still be very helpful for you.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by Bluestars on 2011-04-07
Never mind found a flash drive and using unetbootin.  After I do this will I need to run bootrec /fixmbr from a windows disc?

---

### Post by Bluestars on 2011-04-08
> **aktiwers said:**
> It looks like your partition setup is pretty messed up.

First you need to find out what drive is your Windows Drive. Either try browse through the files on the drives through Ubuntu or boot to Windows and look at the size of your C:\ drive.


 Im pretty sure that the 508gb disk is your windows though.
 
When you know this, I would recomment doint a clean install.
When the installer hits the partitioning menu, pick Manual Partioning.

Now delete alle partitions that are NOT your Windows Partition(all data will be LOST on those partitions). [COLOR=Red]So remember to backup if you have stuff you dont want to loose![/COLOR]
  After this you have 1 NTFS partition (your windows Partition) and a big chunk of empty space.


 
First create a 1gb SWAP partition.
Next create a 30gb EXT4 partition and in mountpoint type:
```
/
``` Next create EXT4 partion on the remaining space, and in mountpoint type:  
 ```
/home
``` You have now created a 1 gb Swap partiton (its like the page file in windows, used instead of RAM when needed). You have a system disk / on 30gb, for Ubuntu and the rest of the space is your /home partiton.
 

 Thats what I would do.

Edit:
Sadly you cant play 3D heavy games in VMware. It runs of a virtual video card and it cant performe 3D as well as your real video card

Got it installed but now when I boot it asks me if I want to boot Ubuntu or Windows 7. Usually if I pick windows it will boot. If I pick Ubuntu it takes me to a list of Ubuntus then loads. Now if I pick Ubuntu it takes me to an error that says windows failed to start and i need to use windows disc to repair. if i pick windows though, windows will boot fine.

---

