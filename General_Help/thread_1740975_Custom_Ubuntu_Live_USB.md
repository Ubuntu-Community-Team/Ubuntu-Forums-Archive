---
title: "Custom Ubuntu Live USB"
date: 2011-04-27
forum: General Help
---

### Post by TheNewbieGeek on 2011-04-27
Hey linux users,

I have found a great article of how to do it online but it only tells me how to make a live cd how can I put it on a usb stick. a link would be great thanks. 

[http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd)

Also in the article you install skype etc. but where did they get the path to donload skype etc. I might want to add more software.

thanks dudes.

---

### Post by bodhi.zazen on 2011-04-27
Best way by far, IMO, is to use the debian-live scripts to build a custom iso.

The take some time to learn, but no more then the method you are looking at, and much of the process is scripted.

If you must, read these pages:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I used to do that ^^

Now I do this :

[http://manpages.ubuntu.com/manpages/lucid/man7/live-helper.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/live-helper.7.html)

[http://live.debian.net/manual/en/html/live-manual.html](http://live.debian.net/manual/en/html/live-manual.html)

---

### Post by C.S.Cameron on 2011-04-27
You can make a Live USB that saves changes using Startup Disk Creator on the Live CD or extract usb-creator, (for Windows), from the iso.
When creating the Live USB select "exra Space" for up to 4GB of persistence.
For Skype etc just get install using synaptic.

If you want to be able to update and upgrade and install proprietary drivers you can do a Full install:
Following a step by step for installing 8.04 on a 8GB flash drive.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by btindie on 2011-04-27
You can use a program called [UNetbootin]("http://unetbootin.sourceforge.net/") to create a bootable USB stick, just point it at your ISO and it'll do the rest.

See this [link]("https://help.ubuntu.com/community/Installation/FromUSBStick#Create%20Bootable%20USB%20Manually") to manually create a bootable USB stick using the generated ISO. This method uses Grub4Dos but you can do the same using syslinux.

For skype, download it directly from their website. Replace the wget command in the article with one of the following depending on your version:

i686: ```
wget --content-disposition http://www.skype.com/go/getskype-linux-beta-ubuntu-32
```x86_64: ```
wget --content-disposition http://www.skype.com/go/getskype-linux-beta-ubuntu-64
```

Also see this [link]("https://help.ubuntu.com/community/USB%20Installation%20Media") to boot an ISO from USB.

---

### Post by TheNewbieGeek on 2011-04-27
Thanks for the links...I want to make a live cd instead because I am sick of viruses. I don't want a persistent install...thank you.

---

### Post by bodhi.zazen on 2011-04-27
> **TheNewbieGeek said:**
> Thanks for the links...I want to make a live cd instead because I am sick of viruses. I don't want a persistent install...thank you.

Live CD are fun and again, if I were to start again, I would stay with the debian-live scripts, that method is easier.

I would caution you of two things:

1. Live CD do take a few hours / days to learn to build. The reason I gave you links is that information will get you started. I consider the information on building live CD to be incomplete and out of date in places, but those links are the best I have. You will need to to a bit of reading to accomplish your task, but post back if you have a specific question.

2. There are no known active viruses for Linux and I would not build a custom CD for fear of viruses, I would direct you to the [Security Sticky](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by TheNewbieGeek on 2011-04-27
Bodhi-zazen:

I decided to use the article you provided. I will need some help completing it.

I ran these commands and received a error.

mkdir mnt
sudo mount -o loop ubuntu-10.10-desktop-i386.iso mnt

the error was:

ubuntu-10.10-desktop-i386.iso: No such file or directory

I imagine the mnt directory might have been created in the wrong location or something. I am following directions precisely and an not changing directories etc.

---

### Post by bodhi.zazen on 2011-04-27
You need to use the full path and correct name to the iso.

Perhaps 

mount ~/Downloads/ubuntu-10.10-desktop-i386.iso /mnt

Notice the / in front of "mnt" and "~/Downloads" in front of the name of the iso.

---

### Post by TheNewbieGeek on 2011-04-27
Actually I decided to use debian live scripts as you suggested it's easier. If I have any questions I'll let you know thank you

---

### Post by bodhi.zazen on 2011-04-27
Just put ubuntu-desktop in the package list and it will pull all the dependencies.

Or use a custom list of packages =)

---

### Post by MBybee on 2011-04-27
I do this to maintain my team's emergency boot disks - and I use Remastersys (to create the ISO), and the Startup Disk Creator to make the USB.

Couldn't be easier.

---

### Post by bodhi.zazen on 2011-04-27
> **MBybee said:**
> I do this to maintain my team's emergency boot disks - and I use Remastersys (to create the ISO), and the Startup Disk Creator to make the USB.

Couldn't be easier.

Excellent suggestion. Remastersys is easy to use and will make a snapshot of your current install.

---

### Post by TheNewbieGeek on 2011-04-27
Thanks Yeah I was thinking of using that software...but I just recently had to replace a computer it broke for unknown reasons could've been a hacker really don't know....so since it uses a current install I thought it might bring the viruses whatever with it when I make the live usb...will it? I am going to use a custom live usb until at least I know more about how to secure my linux computer...I have heard linux is safe right out of the box so I did not bother because I was busy.

---

### Post by bodhi.zazen on 2011-04-28
It takes a little time to learn to use the debian - live scrips, but, if you are wanting a custom iso, the live scripts are , IMO, better / easier / faster then remastersys.

Remastersys is better, IMO, for backups or if you do not really want to learn the details of re-mastering a live ISO.

---

### Post by MBybee on 2011-04-28
> **bodhi.zazen said:**
> 
Remastersys is better, IMO, for backups or if you do not really want to learn the details of re-mastering a live ISO.

I agree entirely. Remastersys is for doing no-fuss images or backups. To seriously do real ISO mastering for large scale use, it's worth learning live scripts.

---

### Post by grubu on 2011-07-15
Also agreeing, learning live scripts seems to be not that difficult and the results will
exactly meet your required decisions for an individual live-distro :D.

---

