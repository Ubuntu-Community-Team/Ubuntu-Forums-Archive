---
title: "How to use and run partimage in Ubuntu"
date: 2009-08-27
forum: General Help
---

### Post by oldtraveler on 2009-08-27
[COLOR="Red"]**Problem solved in #14 below by using CloneZilla**[/COLOR]

I am trying to 1st create an image of my existing Ubuntu installation of 9.04 and 2nd test that image by using it to restore the Ubuntu installation.

Using instructions from [www.psychocats.net/ubuntu/partimage](www.psychocats.net/ubuntu/partimage) I have booted from my live CD, found the terminal and entered 
[color=red]ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get install partimage[/color]

Pressing enter I get:
 
[color=red]Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release [74.6kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [49.6kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [87.4kB]        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages [1253kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages [8848B]            
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources [555kB]              
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2589B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [23.7kB]        
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [623B]    
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources [3156B]             
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages [160kB]          
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages [2589B]    
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources [44.9kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources [623B]
Fetched 2316kB in 5s (389kB/s)                           
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package partimage is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package partimage has no installation candidate
ubuntu@ubuntu:~$ [/color]


Thus I have no way to continue following the instructions.  
Thinking that perhaps I should run partimage directly from the Ubuntu installation I tried that only to be stumped when I received an error message stating that the drive to be imaged was mounted and that it needed to be unmounted.  Whoa!

Your suggestions please.

---

### Post by bchurchill on 2009-08-27
Usually this type of problem is solved by editing /etc/apt/sources.list (make a backup first!) and uncommenting some universe repositories and running sudo apt-get update again...

...But I remember I struggled with partimage for a while.  there were some odd issues.  I think I got it running on Ubuntu once... I think I compiled it from source from partimage's website (a bit of work, you'll need to install dependencies manually).

An easy thing to do is download SystemRescueCD.  It's a gentoo-based live CD that has partimage and several other nice utilities: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page).  I've found it to be very convenient.

  You could also try downloading the debian package from packages.ubuntu.com but this may be more work, I don't know.

---

### Post by SPr on 2009-08-27
If you use PartImage from the Ubuntu CD you will have to download and install it every time you want to run it. Search Google for SystemRescueCD which is a bootable CD with Partimage already installed.

Partimage is in "universe" ([http://packages.ubuntu.com/ko/jaunty/partimage](http://packages.ubuntu.com/ko/jaunty/partimage)) edit /etc/apt/sources.list.

---

### Post by oldtraveler on 2009-08-27
OK.  Trying to use the SystemRescueCD which I created from the iso file. It takes forever to boot, but eventually I get to a linux distro that contains PartImage.  First I created a 16GB partition on my external drive and formatted as ext3. That is /dev/sdc2

When I try to create an image to be sent there I get the following error:
"Cannot create temp file [/dev/sdc2/pi964a7135.tmp] Please check there is space enough and you have access rights."

What now?

In this regard I do notice that when I try to access that partition from my installed Ubuntu 9.04 it says that the owner is root.  I have been advised not to set up Ubuntu for root - so how do I get permission to work with that partition?

---

### Post by piemonkey on 2009-08-27
I've not used SystemRescueCD, I use Parted Magic, but I assume it's similar.

If I read correctly, you're trying to backup your Ubuntu 9.04 install to /dev/sdc2. First, when you've booted into SystemRescueCD, you'll want to make sure that /dev/sdc2 is mounted, and your Ubuntu partition is not. That sounds to me like it's the source of the error you've given above.
mount /dev/sdc2
or
sudo mount /dev/sdc2
(if it tells you that you need to be root) will mount the drive (probably at /media/sdc1) and then you can tell partimage to put the image there.

---

### Post by bchurchill on 2009-08-27
> **oldtraveler said:**
> 
When I try to create an image to be sent there I get the following error:
"Cannot create temp file [/dev/sdc2/pi964a7135.tmp] Please check there is space enough and you have access rights."

What now?

In this regard I do notice that when I try to access that partition from my installed Ubuntu 9.04 it says that the owner is root.  I have been advised not to set up Ubuntu for root - so how do I get permission to work with that partition?

At the very least, when you mount and backup you'll need root access.

As you mentioned, Ubuntu should not be setup for root access, and your daily use of Ubuntu shouldn't require root (maybe a few sudos...).  However, just about everything you do on the restore CD will require root access, either via sudo or otherwise (mounting drives, and backing them up).  Personally I recommend loging in as root when using the SystemRescueCD, as this will solve many problems (and it's a Gentoo live CD, makes a bit more sense).  Obviously, be very careful.  Unfortunately I can't think of a much better way of doing this.  You could just use sudo on every command... but at that point it's essentailly the same thing.

The other possibility is that your 16GB drive is full.  One of the two is the culprit, probably the permissions.

---

### Post by drs305 on 2009-08-27
piemonkey probably addressed the problem. It sounds like the backup partition wasn't mounted.

Here is another partimage howto:
[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html]("http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html")

---

### Post by oldtraveler on 2009-08-29
I feel like I am so close to getting partimage to create an image but......

I have created additional ext3 partitions on both my internal hd as well as my external hd for a location to store the image.  I continue however to get the error message 
"Cannot create temp file [/dev/[color=red]sdc2[/color]/pi964a7135.tmp] Please check there is space enough and you have access rights." where [color=red]sdc2[/color] can be sdb5 or whatever my desired storage partition is.

I can't find out how to mount and unmount partitions and using the SystemRescue CD there doesn't seem to be a way to do it. If I try to create an image from the installed Ubuntu 9.04, then isn't it mounted and must remain so?

---

### Post by drs305 on 2009-08-29
> **oldtraveler said:**
> I can't find out how to mount and unmount partitions and using the SystemRescue CD there doesn't seem to be a way to do it. If I try to create an image from the installed Ubuntu 9.04, then isn't it mounted and must remain so?

When I start the SystemRescue CD it boots to a command prompt. Before starting my backup app (partimage), I:
```

mkdir /mnt/temp
mount /dev/sdb1 /mnt/temp  # /dev/sdb1 is my backup partition
partimage

```
Note: If you are mounting an NTFS partition, the command is:
```
mount -t ntfs-3g /dev/sdXX /mnt/temp
```
Select the partition to save with up/down arrows
The file pathname must be included in the name: "*/mnt/temp/*backup-filename"
Tab through the options, select/deselect with the space bar 
Just before I hit 'OK', I check to see the estimated free space. Once it starts, check the 'Available Space for Image' as it starts to write.

---

### Post by bchurchill on 2009-08-29
> **oldtraveler said:**
> I feel like I am so close to getting partimage to create an image but......

I have created additional ext3 partitions on both my internal hd as well as my external hd for a location to store the image.  I continue however to get the error message 
"Cannot create temp file [/dev/[COLOR=red]sdc2[/COLOR]/pi964a7135.tmp] Please check there is space enough and you have access rights." where [COLOR=red]sdc2[/COLOR] can be sdb5 or whatever my desired storage partition is.

I can't find out how to mount and unmount partitions and using the SystemRescue CD there doesn't seem to be a way to do it. If I try to create an image from the installed Ubuntu 9.04, then isn't it mounted and must remain so?

This looks like the same problem as before.  /dev/sdc2 is not a mount point, it's a device file.  Follow the instructions from the above posters carefully, and specify your mount point (e.g. /mnt/temp/.....) rather than the device file.

---

### Post by oldtraveler on 2009-08-30
Thanks for all of your patience and suggestions.  I don't completely understand what you are saying about mount points, but I managed to get a restorable image of Ubuntu 9.04 created from my Windows installation using Paragon Hard Disk Manager. Since I am familiar with this program it was a piece of cake.

---

### Post by piemonkey on 2009-08-30
> **oldtraveler said:**
> If I try to create an image from the installed Ubuntu 9.04, then isn't it mounted and must remain so?

If you mean create an image *of* the installed Ubuntu (sorry to be pedantic, but it does make a difference to the meaning), then no, partimage works with the blocks of the filesystem, not with the files, so it doesn't need to be mounted.

If you're having trouble with SystemRescueCD I'd recommend Parted Magic. It has a lot more graphical interface, including a graphical mounting tool, and automatic network configuration. You can find it here [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

---

### Post by piemonkey on 2009-08-30
Curses, I got here too late, proprietary software beat me to it...

But seriously, mounting is one of those things with linux/unix that it helps to understand, I'd recommend having a look at this, at least the first part [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount) should give you a better idea of what we were talking about.

---

### Post by oldtraveler on 2009-09-17
Problem solved by downloading CloneZilla iso file and creating a CD.  Boot from CD and can then create image of partition and subsequently restore that partition from the saved image

---

