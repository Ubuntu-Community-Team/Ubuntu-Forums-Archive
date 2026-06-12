---
title: "Problem with login on fresh installed system"
date: 2009-11-18
forum: General Help
---

### Post by alexandr.imzailov on 2009-11-18
I have a problem. I have several times to choose your username and a password to access the system via gdm. And the data I enter correctly. I have no problems can go into the system through the terminal ([ctrl] + [f1]), but when I enter the command 'sudo restart gdm', I see on the screen menu entry instead of the desktop. I did check partitions / dev/sda2 (/) and / dev/sda7 (/home) with a live-cd xubuntu 9.10 x86_64, it showed that there are no problems with the file system. Today, I specifically _slowly_ enters a password and in general all of the menu entry I did slowly and can therefore I had to enter the password 2 times against the usual 8-12.
I installed the system almost from scratch (I did not upgrade system and redistributed free disk space and installed system in free space), sections /dev/sda2 and /dev/sda7 formatted in ext4. I had exactly the same problem after upgrade system with ubuntu 9.04 to 9.10, when the fs was on the disk ext3.
Now I have installed the latest updates and uses a video driver nv.
P.S.
(Sorry if that for English, translated the message through a machine translator.)

---

### Post by wrgb2 on 2009-11-18
Your post is labeled Xubuntu, yet you are talking about gdm.  Did you install xubuntu, then install gnome desktop manager?

---

### Post by alexandr.imzailov on 2009-11-19
I did't install gnome desktop, I am use XFCE4.

---

### Post by efflandt on 2009-11-19
I had a similar problem with Xubuntu 9.10 on an older PC (PIII 550 w/320 MB RAM).  It seemed to take forever for Xubuntu to come up from install CD, but then install seemed to work fine and I was able to reboot from it fine.

But after installing updates, when I tried to log into xfce it would start to load something, then go back to the fireflys or glowing gnats or whatever, and bring up login again.  When I intentionally entered a wrong password, it instead immediately told me that login failed.  I was able to log into xterm, or go to a console with Ctrl-Alt-F2 and log into that, so I knew my password was good.

If you can log into xterm or a console, see if **dmesg | less** shows any errors, or **less /var/log/messages** or other files in /var/log.

Mine seemed to indicate problems reading /dev/hda3 where / is, which is no surprise, because I initially had trouble partitioning and ext3 formatting anything past some point on the hard disk.  For example when I initially tried to format nearly half ext2, swap, and other half ext3 from gparted-live CD, sda3 ended up showing as unknown partition type or filesystem.  When I formatted 40 GB + 2 GB swap, leaving the remainder unassigned, it also failed.  It worked with 30 GB sda1 and 2 GB sda2 swap, and Ubuntu Jaunty runs fine from there.  When I later added sda3 as ext3 that "appeared" to work.  But Xubuntu 9.10 running from there apparently has problems since it tried to add packages to bad sectors.

I am currently running e2fsck -cckfv /dev/sda3 to try to mark bad blocks.  But that has been going for almost 12 hours and is less than 45% completed.  So I guess the tail end of that drive is unusable.

But without looking at your logs, we cannot really say if you have a video driver or other hardware problem, or a bad drive.

Have you run memtest86+ on that computer to make sure that its RAM (memory) works with that PC?

---

### Post by alexandr.imzailov on 2009-11-23
After an unsuccessful login (the password I entered correctly). I went into the terminal ([ctrl] + f1]) and copied the folder /var/log and output of dmesg. You can download the logs /var/log [here]("http://ifile.it/5e3qfsg"). From [here]("http://ifile.it/pe2s3tf") you can download the output dmesg(I copied it, after a successful login).  I ran memtets86 + and it is to report that no errors were found.
Hard drive not tested yet.
[IMG]http://www.google.ru/images/cleardot.gif[/IMG]

---

### Post by alexandr.imzailov on 2009-12-05
I tested the hard drive for bad blocks using Victoria 3.53 and she reported that the defects are not detected.

---

### Post by azertyh on 2009-12-05
hello,
i had the same problem and we are not the only person who have it.
i re-installed many times xubuntu, i can connect to the desktop after the re-installation but at reboot, the problem appears.
someone wrote that it is resolution problem and i remember that i always set the screen resolution at my first connection to the desktop.
so, i re-installed xubuntu thursday, i didnt set the screen resolution and now, it's ok. perhaps, it can help you. it's not a definitive solution but it works.

another solution that i find is to set the screen resolution in a terminal with the command xrandr. i dont try it yet. so i dont know if it works or not.

---

### Post by azertyh on 2009-12-11
hi,

see this topic to log on to the desktop : [http://ubuntuforums.org/showthread.php?p=8402051#post8402051](http://ubuntuforums.org/showthread.php?p=8402051#post8402051)

---

### Post by Freedom Sky on 2010-01-01
**alexandr.imzailov**

Sorry for offtop, but if you are from Russia - contact me by ICQ. My PC has same problem. Or Or almost the same...

---

