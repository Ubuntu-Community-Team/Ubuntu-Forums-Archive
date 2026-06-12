---
title: "Install Ubuntu after Dual Booting"
date: 2011-07-29
forum: General Help
---

### Post by TheMidnightWings on 2011-07-29
Vauge title, sorry, don't really know how to put this, I dual booted this with windows 7 while in the install because I didn't want to lose Windows. That was two weeks ago, (*installing 10.10 over 11.04*) and I have booted Win7 once in that whole time frame. All my important files have already been imported to Ubuntu, so Win7 at this point is just taking up a shitload of space for no reason. 
Do I have to use*** Gparted*** or what?? I dunno how all this stuff works quite yet, please gimme a hand! :KS Cheers!

---

### Post by lmarmisa on 2011-07-29
First of all, consider if you really need to remove completely Windows 7. Perhaps you could shrink its partition(s) to a minumum size and then reuse the free space for Ubuntu.

Other recommendation is to make a backup of your system before to remove Windows 7. I recommend Clonezilla Live for that complete backup:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

Gparted is a good tool if you are going to edit (create, shrink, enlarge, remove, etc) partitions.

Gparted is included in Ubuntu Live CDs but not in the installations. Type this command for installing Gparted:

```

sudo apt-get install gparted

```

The edition of partitions is a risky operation. So, be very careful, specially with those associated to the Ubuntu OS (root, swap).

---

### Post by TheMidnightWings on 2011-07-29
Thank you for such a quick response, I'll have to try that.. and yeah maybe I'll just shrink the win7 partition, but wouldn't that affect files on my Ubuntu 10.10 too?? :/ Sorry I am not the most computer savvy person you'll ever meet. :confused:

---

### Post by lmarmisa on 2011-07-29
If you shrink the Windows 7 NTFS partition, that operation will not affect to the other partitions of your hard drive(s). 

Anyway, I would like to get some information about the partitions of your hard drive. Please, open a terminal, type these commands and post the results:

```

sudo fdisk -l
sudo parted -l

```

---

### Post by TheMidnightWings on 2011-07-29
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5880    47223551+   7  HPFS/NTFS
/dev/sda2            5880        9730    30925825    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris
/dev/sda6            5880        9180    26508288   83  Linux
/dev/sda7            9180        9327     1184768   82  Linux swap / Solaris
This is the info I got! (No idea what any of it means)

---

### Post by lmarmisa on 2011-07-29
> **TheMidnightWings said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5880    47223551+   7  HPFS/NTFS
/dev/sda2            5880        9730    30925825    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris
/dev/sda6            5880        9180    26508288   83  Linux
/dev/sda7            9180        9327     1184768   82  Linux swap / Solaris
This is the info I got! (No idea what any of it means)

Sorry, the info is not complete. Could you repeat the two commands and post all the information?. Try to use the Wrap CODE tag (**#**).

---

### Post by Mark Phelps on 2011-07-30
Some comments (if you EVER intend to reuse Win7 later) ...

First, do NOT, repeat NOT, shrink it with GParted or any other Linux tool.  Doing so runs the risk of filesystem corruption, which often then renders Win7 unbootable.

Use the Win7 Disk Management utility to do the shrinkage -- but don't be surprised if it won't let you shrink much.  It's infamous for that.

Second, once you get it shrunk, reboot into it a couple of times to let the filesystem do any needed adjustments.

Third, if you really want to remove it, do the following:
1) Download and install the FREE version of Macrium Reflect
2) Use the MR option to create the Linux Boot CD
3) Image off the Win7 install to an external drive

NOW ... you can safely remove Win7 because you have the means to completely restore it in the future, if you need it.

---

