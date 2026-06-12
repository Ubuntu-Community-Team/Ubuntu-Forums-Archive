---
title: "Newbie Help Overload"
date: 2011-10-20
forum: General Help
---

### Post by CountryGuy on 2011-10-20
Hello!

I'm a .NET developer who is looking to get more involved in our Java development, where our app/web servers are running Linux.  As a kind of "immersion" program, I'm going to try setting up my home laptop as a dual-boot box, with Ubuntu being my primary environment (with development VMs for .NET and another for Java), and Windows 7 on the other for when I want to play games on the box - Eventually I'll try wine, but I figure better to learn a bit at a time :)

This isn't for lack of searching, but rather search overload:  I found a LOT of threads on dual booting Win7 and Ubuntu (which speaks good things for the community here!).  Could someone recommend one of the threads here for doing a clean dual-boot environment (starting from scratch on this machine).

*[Edit:  Questions below being moved to separate threads per recommendation - Thanks!]*

Also, I'm curious as to the support for Sandy Bridge architectures, particularly laptops with dual video cards (I have a low-power Intel card, as well as an ATI card for games).  While I have a couple ideas on disabling the ATI card in Linux if need be (as I won't be doing anything graphics-intensive), but I heard my HP laptop has proprietary drivers and hasn't put out anything for Linux, so not sure if I can set up both video cards - But would like to if possible!

Would you recommend Evolution or Thunderbird for IMAP email / contacts / calendar?  I use GMail, but prefer using a client vs. the browser based env.  Also, how easy is it to install Chrome on the 64-bit Ubuntu (not Chromium;  I do use some of Google's proprietary features).

One other question:  Is there a recommended thread for how to configure one's environment for security?  Again, I've seen plenty in a search, but I'm hoping there's a consolidated thread somewhere.  For now, my laptop will be safe behind my home's router / firewall, but eventually I'll want to take it into the big bad world, and want to make sure its locked down safe :)

Finally (for now):  How difficult does SELinux make using Ubuntu?  I know most of our environments at work utilize this kernel enhancement, so wouldn't mind learning the same (as long as it won't make things too difficult).

Thanks in advance!

---

### Post by blueridgedog on 2011-10-20
For dual boot, this is a good resource:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

For the other issues, I suggest you start individual threads.

One item you want to have straight in your mind is the layout you want of your hard drive (what partitions, what size and what use).  As a developer, you may have a great grasp of partitioning, but if you are not comfortable, now is a good time to talk through your plans.

How bid is your hard disk?  Members here can make some suggestions as to how to partition it so you are not stuck in the future.

At a minimum, you will need to reduce your current NTFS partition to make room for at least two (maybe three) new partitions.  The first will be a Linux partition for the installation of Ubuntu and the second will be a small partition for swap space.  The third could be a data partition where you share data between your boot environments.  

Something such as:
First primary is windows
Second primary is an extended
First extended is swap
Second extended is Linux

You can either use all the remaining space in the second (extended partition) or leave some free space in the event that you want to create another primary partition down the road.

---

### Post by CountryGuy on 2011-10-20
/facepalm  Ugh, there is a specific channel for dual boot?  Sorry about not seeing that!

As for partitioning, My plans right now are for four:  Windows 7's System Reserved share (100MB), One partition each for each OS, then a Storage share which will have my data files and Virtual Machines (for when I'm too lazy to connect up my external drive for performance).

My drive is 500GB (7200RPM), so it has ample space to handle both operating systems.  My initial thought was: 
Partition 1:  Ubuntu (as my primary OS)
Partition 2:  Windows 7's System Reserved partition
Partition 3:  Windows 7 (OS)
Partition 4:  Storage

As far as space / storage:
P1: default fs w/ 50GB
P2: 100MB
P3: NTFS w/ 100GB (as I'll have games here, and don't feel like dealing with moving \Program Files\ to another drive)
P4: Remaining 250GB for music, documents, etc...  Not sure if I'll make this FAT32 or NTFS (depends on how easily Ubuntu can read from a NTFS drive)

I have a server at home, so I don't need to store too much locally - Just stuff I need to take with me.  I also have an external USB 3.0 drive for the VMs so they don't hog the laptop's drive.

Does that sound like a solid setup? as far as the drive goes?  Thanks again for the quick response!

---

### Post by 2F4U on 2011-10-20
I think you should - as the guide states - install Windows first and Ubuntu as a second step. Else you will probably get problems with Windows overriding Ubuntu's boot loader.

---

### Post by CountryGuy on 2011-10-20
> **2F4U said:**
> I think you should - as the guide states - install Windows first and Ubuntu as a second step. Else you will probably get problems with Windows overriding Ubuntu's boot loader.

Yep, read through the page and saw that.  I'm pretty sure Win7 will try and force partition 1 to be its 100MB System Reserved partition, in which case I'll have to swap that with the Ubuntu partition number.

As far as partition sizes go, does 50GB sound sufficient for installed apps (with data going to the Storage partition)?  I think I saw it only needs 15GB, but I want to leave room for expansion / new app installations.

---

### Post by 2F4U on 2011-10-20
I sometimes use 10GB as root partition and never had problems. But I usually have a separate /home partition for data and I don't install much software. 50GB should be more than sufficient.

---

### Post by blueridgedog on 2011-10-20
Given that you will need a swap partition and will need to install windows first, I recommend:

Primary 1 sda1: windows reserved 100mb
Primary 2 sda2: windows 7 os 100GB
Primary 3 sda3: Extended Partition - Remainder of disk 300 GB
Extended 1 sda5: Linux 50 GB
Extended 2 sda6: Linus Swap 4 GB
Extended 3 sda7: Remainder for Files 250 -+

I recommend creating these first with a LiveCD and then telling each installer where to install and where to format.

---

### Post by CountryGuy on 2011-10-21
Aha, forgot about swap space, thanks for the reminder!

As far as the data partition goes (shared stuff between Linux and Windows), what's the recommendation as far as filesystem?  I know FAT32 will work between both;  Is NTFS an alternative that works with Linux?

---

### Post by WasMeHere on 2011-10-21
> **CountryGuy said:**
> Aha, forgot about swap space, thanks for the reminder!

As far as the data partition goes (shared stuff between Linux and Windows), what's the recommendation as far as filesystem?  I know FAT32 will work between both;  Is NTFS an alternative that works with Linux?
Yes, NTFS is OK and it is good to use *windows_names* to make sure that Ubuntu does not allow you to enter file names that cannot be read by Windows according to the following thread. (Apply the correct partition number for ***your*** data partition!)
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11342282&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11342282&postcount=5")

Good luck :-)
Olle

---

