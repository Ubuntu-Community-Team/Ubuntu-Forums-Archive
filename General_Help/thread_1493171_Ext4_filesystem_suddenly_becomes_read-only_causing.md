---
title: "Ext4 filesystem suddenly becomes read-only causing crash"
date: 2010-05-25
forum: General Help
---

### Post by elijah-man on 2010-05-25
OK, so been running 9.10 for a while now (been using Ubuntu for over 2 years and on 3 different laptops), but I have suddenly started having trouble with my file-system.  All of a sudden my computer will lock up without warning and I can't do anything.  I have to hard-reboot, run FSCK as root, then reboot again to get it back up.  I originally thought it was Firefox so I started using GoogleChrome to see if that made a difference, but that crashed it too.  I was then using Rapid Photo Downloader today and about half way through it encountered an issue and skipped the rest of the files.  I looked at the error message and found that my file-system decided to become read-only all of a sudden.  As expected, everything pretty much locked up and crashed.  I had to do a hard-reboot, FSCK, and reboot again to get back to where I am now.  I am running 9.10 (fresh install, not upgraded) with an encrypted EXT4 file-system.  Like I said, I have been running 9.10 on this machine for several months, but just started having issues last week and the crashes are getting progressively more frequent.  Not sure if it has to do with EXT4, the fact that my file-system is encrypted, Grsync, an updated kernel, or something else completely.  Please help!
I'm obviously not a Linux wizard, but if you give me something to input into terminal I can give you the output.
Thanks, Eli

---

### Post by blueturtl on 2010-05-25
Have you considered the possibility of hardware failure?

Randomly appearing and progressively worsening problems with a file system is a strong indicator that there might be something wrong with the hard drive.

---

### Post by elijah-man on 2010-05-26
I had considered it, but the hard drive is only a few months old.  Do hard drives go bad that quickly?  It's a 320GB WD Scorpio 7200rpm.  I keep all my files backed up, so it's not the end of the world if the hard drive dies, but it sure is annoying.  Is there any command line program (or GUI) I can run to test if it's hardware failure?
Thanks, Eli

---

### Post by bodhi.zazen on 2010-05-26
> **elijah-man said:**
> I had considered it, but the hard drive is only a few months old.  Do hard drives go bad that quickly?  It's a 320GB WD Scorpio 7200rpm.  I keep all my files backed up, so it's not the end of the world if the hard drive dies, but it sure is annoying.  Is there any command line program (or GUI) I can run to test if it's hardware failure?
Thanks, Eli

Smartmontools

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by blueturtl on 2010-05-27
> **elijah-man said:**
> I had considered it, but the hard drive is only a few months old.  Do hard drives go bad that quickly?  It's a 320GB WD Scorpio 7200rpm.  I keep all my files backed up, so it's not the end of the world if the hard drive dies, but it sure is annoying.  Is there any command line program (or GUI) I can run to test if it's hardware failure?
Thanks, Eli

You might have a so called 'lemon' on your hands. Normally hard drives last 5 years and upwards (heck, I even know functional 40 MB hard drives!) but sometimes you just end up with a bad individual.

S.M.A.R.T. maybe able to tell you if the hard drive is dying but it is not completely accurate (only works if the HDD itself knows it is dying).

Problems like yours are really tough to trouble shoot because there are so many things that could potentially be causing data corruption. The only way to trace the problem is to be throrough and systematic.

What are the last software/hardware alterations you have done on your set up? Is the last change within a reasonable time frame of the onset of this problem?

---

### Post by StuartN on 2010-05-27
> **elijah-man said:**
> All of a sudden my computer will lock up without warning and I can't do anything.  I have to hard-reboot, run FSCK as root, then reboot again to get it back up.

You can search these forums for "freeze" to find many similar reports. Installing the mainline 2.6.34 kernel worked for my machines (see [http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html)).

EDIT: 2.6.34 for Ubuntu 10.04 Lucid, but use 2.6.33 for Ubuntu 9.10 Karmic

---

### Post by elijah-man on 2010-05-27
> **blueturtl said:**
> 
What are the last software/hardware alterations you have done on your set up? Is the last change within a reasonable time frame of the onset of this problem?

Hardware has been the same since I first got the computer several months ago (I immediately pulled out the original hard drive loaded with Win-7 and stuck in a new one to load with 9.10 so I can re-swap drives when I want to sell the computer).  The HD and the computer are both under warranty, so if it's a hardware issue, I should be covered.

The only software changes I made since I first got my system up and running were through update manager.  I have a large set of programs that I like and re-install every time I wipe my drive and re-install an operating system.  Many of the programs I use are through PPA's, but they are all fairly mainstream (eg. Wine).  I guess it could be related to a program or kernel update, but I would not know which one it could possibly be.

I will install and run SMART so see if that gives me anything and report back.

-Eli

---

### Post by piginabox on 2010-10-13
I've had this with two WD Blue Scorpio 500GB 2.5 drives.
They kept failing and being forced to read-only mode when writing data to them. Sometimes they'd work fine for days then fail.
I tried ext2,ext3,ext4 and got similar results with both drives.
When formatted to ntfs they worked fine.
The upside is that WD had sent a replacement drive without asking for the original back, hence having two identical drives.

---

