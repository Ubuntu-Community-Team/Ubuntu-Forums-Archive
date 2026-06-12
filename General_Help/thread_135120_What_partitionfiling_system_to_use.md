---
title: "What partition/filing system to use ?"
date: 2006-02-23
forum: General Help
---

### Post by wpshooter on 2006-02-23
1) Can someone tell me what file system I should use for Ubuntu partition to make it compatible with my Win2000 install which is using NTFS ?   Which of the below would be the most compatible and give the best performance from Ubuntu ? 

I see that there are 10 file system choices on the Ubuntu install including Ext3, Ext2, Resier, JFS, XFS, FAT16, FAT32, SWAP, VLM, & RAID.

I tried the Ext3, but when I booted back into Windows, it did not seem to like that very well, i.e. Windows had problems recognizing that filesystem.

2) Is there some way other than having to do a mount command from the terminal each boot to get the Ubuntu system to recognize the floppy drive ?  I can format the floppy in the drive just fine but if I try to right click on the drive and mount it, it says that I can not do it.  I see that there is an update, which the system is showing called something like pmount.  Is this application what fixes the floppy mounting problem ?

3) Also, can someone tell me what the root user (ADMIN) name is and the accompanying password.  I do not like the idea of having to go back and forward between a limited user and the ADMIN user.  I run as admin on all of my Windows system and I have never had any problems.  I tried root as the user and root and the password but it does not work.  What is name and password or is this not doable ?

Thanks.

---

### Post by jbennett on 2006-02-23
[QUOTE=wpshooter]1) Can someone tell me what file system I should use for Ubuntu partition to make it compatible with my Win2000 install which is using NTFS ?   Which of the below would be the most compatible and give the best performance from Ubuntu ? 

I see that there are 10 file system choices on the Ubuntu install including Ext3, Ext2, Resier, JFS, XFS, FAT16, FAT32, SWAP, VLM, & RAID.

I tried the Ext3, but when I booted back into Windows, it did not seem to like that very well, i.e. Windows had problems recognizing that filesystem.

2) Is there some way other than having to do a mount command from the terminal each boot to get the Ubuntu system to recognize the floppy drive ?  I can format the floppy in the drive just fine but if I try to right click on the drive and mount it, it says that I can not do it.  I see that there is an update, which the system is showing called something like pmount.  Is this application what fixes the floppy mounting problem ?

3) Also, can someone tell me what the root user (ADMIN) name is and the accompanying password.  I do not like the idea of having to go back and forward between a limited user and the ADMIN user.  I run as admin on all of my Windows system and I have never had any problems.  I tried root as the user and root and the password but it does not work.  What is name and password or is this not doable ?

Thanks.[/QUOTE]

Alright, I'll break it down into the parts you listed.

1.  The filesystem for Linux is ext3 (or the older ext2) so your Ubuntu install will have to be on an ext3 partition.  You're right, Windows won't recognize this.  In order to share files between OS's you will need to also create a fat32 partition.  This will allow you to save things in Windows and then use them in Ubuntu or vice versa.  (Note that Ubuntu will recognize and read an NTFS partition but *will not *write to it) Check out this link: [Mouting Windows Partitions in Ubuntu]("http://www.psychocats.net/linux/mountwindows.php") by Aysiu.  It does a good job of explaining how to modify permissions, etc.

2.  Check out [this thread.]("http://www.ubuntuforums.org/showthread.php?t=104259&highlight=howto+mount+floppy")

3.  Read [this guide to editing files with root priviledges]("http://www.psychocats.net/linux/permissions.php") and take a look at [this wiki.]("https://wiki.ubuntu.com/RootSudo")

Hope that helps.  These are the threads and howtos that I found really helpful when I was installing Ubuntu about a week ago. :)

---

### Post by suRoot on 2006-02-23
[QUOTE=wpshooter]1) Can someone tell me what file system I should use for Ubuntu partition to make it compatible with my Win2000 install which is using NTFS ?   Which of the below would be the most compatible and give the best performance from Ubuntu ? 

I see that there are 10 file system choices on the Ubuntu install including Ext3, Ext2, Resier, JFS, XFS, FAT16, FAT32, SWAP, VLM, & RAID.

I tried the Ext3, but when I booted back into Windows, it did not seem to like that very well, i.e. Windows had problems recognizing that filesystem.

[/QUOTE]

Windows won't natively recognize any linux filesystem.  You can read ext2/ext3 partitions & reiser partitions under windows, but you need to install a driver or utility to do so.

See this to read ext2/ext3 under windows:
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

See this to read reiser under windows:
[http://p-nand-q.com/download/rfstool/download.html](http://p-nand-q.com/download/rfstool/download.html)
[http://yareg.akucom.de/index.html#FEATURES](http://yareg.akucom.de/index.html#FEATURES)

If you want to set up a drive to share data between windows & linux, format it as fat32.

---

### Post by Karlos on 2006-02-23
> 3) Also, can someone tell me what the root user (ADMIN) name is and the accompanying password. I do not like the idea of having to go back and forward between a limited user and the ADMIN user. I run as admin on all of my Windows system and I have never had any problems. I tried root as the user and root and the password but it does not work. What is name and password or is this not doable ?

if your fairly new to linux then don't run as root all the time.
once your experienced at linux you just wouldn't run as root unless you need to.
but ..
in answer to the question
yes you can run as root

for example: if you are using a terminal and want to become root then do
```
sudo -s -H
```
this will make you the root user for that terminal session

if you want to create a root user then do
```
sudo passwd root
```
and enter a password for root

you can then enable root to log in through GDM (System > Admin > Login Screen Setup)

then you can actually log in as root into a gnome desktop (just for admin purposes of course)

hope that helps .K.

---

### Post by wpshooter on 2006-02-23
I am NOT trying to share anything between the two O/S (or at least not intentionally).

When I rebooted into Windows, during the boot process Windows wanted to do a scan disk on the Ubuntu partition and then could not.  Then when I got to the desktop and tried to open my computer it took a tremendous amount of time for it to display the drive info (this is not normal).  It's as if it is try to understand the info on the Ubuntu partitions and CAN'T.  Is there any possibility that I have done any damage to my Windows O/S by putting the Ubuntu on as an EXT3 file system ?

Thanks.

---

### Post by jbennett on 2006-02-23
[QUOTE=wpshooter]I am NOT trying to share anything between the two O/S (or at least not intentionally).

When I rebooted into Windows, during the boot process Windows wanted to do a scan disk on the Ubuntu partition and then could not.  Then when I got to the desktop and tried to open my computer it took a tremendous amount of time for it to display the drive info (this is not normal).  It's as if it is try to understand the info on the Ubuntu partitions and CAN'T.  Is there any possibility that I have done any damage to my Windows O/S by putting the Ubuntu on as an EXT3 file system ?

Thanks.[/QUOTE]

hmmmm.  I didn't have any trouble installing Ubuntu on an ext3 partition.  When I boot Windows it displays my newly resized ntfs partition and a fat32 partition.  I'm afraid I don't know the answer to that question.  Have you tried searching the forum for related topics?  Chances are someone has had a similar problem in the past.  

Maybe installing the drivers mentioned in a previous post by SuRoot would solve the problem.

---

### Post by cotcot on 2006-02-23
For shared files : Fat if you do not have single files larger than 4 GB or ext2 (no single file size limit). Accessing ext2 from 2000 or XP need the installation of an ext2 driver in XP/2000. This is simple to do. Download and instructions : see  [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by lamego on 2006-02-23
There is something missing on your story.
Windows would not try to scandisk a partition which it is not able to identify (ext3).
Also it should not try to access the ext3 partitions as it seems to be happening when you browse on windows.
Did your previously had a windows partition where you lately installed linux ? If yes probably there was an extended partition info which you have not deleted and which is "informing" windows about the older partition which does no longer exist. (not on a known format for it).

---

### Post by wpshooter on 2006-02-23
[QUOTE=Karlos]if your fairly new to linux then don't run as root all the time.
once your experienced at linux you just wouldn't run as root unless you need to.
but ..
in answer to the question
yes you can run as root

for example: if you are using a terminal and want to become root then do
```
sudo -s -H
```
this will make you the root user for that terminal session

if you want to create a root user then do
```
sudo passwd root
```
and enter a password for root

you can then enable root to log in through GDM (System > Admin > Login Screen Setup)

then you can actually log in as root into a gnome desktop (just for admin purposes of course)

hope that helps .K.[/QUOTE]

I am sure it will, I will try it when I get home.  Thanks.

---

### Post by wpshooter on 2006-02-23
[QUOTE=lamego]There is something missing on your story.
Windows would not try to scandisk a partition which it is not able to identify (ext3).
Also it should not try to access the ext3 partitions as it seems to be happening when you browse on windows.
Did your previously had a windows partition where you lately installed linux ? If yes probably there was an extended partition info which you have not deleted and which is "informing" windows about the older partition which does no longer exist. (not on a known format for it).[/QUOTE]

Yes, I had just thought about this before I came back in to check the post.  I had had two open partitions E & F on the drive and I had formatted them from Windows FAT32 just last week, looks like I should have held off on that and just left them partitioned and not formatted.  O Well back to the drawing board, chalk it up to experience.

Thanks.

---

### Post by pellgarlic on 2006-05-17
[QUOTE=wpshooter]Yes, I had just thought about this before I came back in to check the post.  I had had two open partitions E & F on the drive and I had formatted them from Windows FAT32 just last week, looks like I should have held off on that and just left them partitioned and not formatted.  O Well back to the drawing board, chalk it up to experience.

Thanks.[/QUOTE]

lamego is right - if i were you, when/if you install ubuntu again, don't even create a partition in windows - just delete the partition where you want ubuntu to go (N.B. make sure to delete the right partition so you don't lose anything you want to keep!) and leave it "unallocated space". then when you run the ubuntu setup, use the built-in partition manager to create and format the partition using the "unallocated space". this will certainly avoid any issues with residual "extended partitions".

---

