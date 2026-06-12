---
title: "How to edit size of partitions?"
date: 2011-07-24
forum: General Help
---

### Post by mattdee132 on 2011-07-24
When I installed Ubuntu, I dual booted with Windows, but now I want to get rid of my Windows partition and only use Ubuntu.  There are no important files on the Windows partition, so I am just looking to delete it and then expand the Ubuntu partition to fill that space.  How does one go about doing that?

my hard drive looks like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3            1918       26023   193623018    7  HPFS/NTFS
/dev/sda4           26023       38914   103546881    5  Extended
/dev/sda5           26023       38658   101490688   83  Linux
/dev/sda6           38658       38914     2055168   82  Linux swap / Solaris

---

### Post by frankbooth on 2011-07-24
You'll find a detailed guide on how to resize partitions here: [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

If there's something you don't understand or if you need further help, just ask :).

**[SIZE="3"][COLOR="Red"]REMEMBER! BE CAREFUL WHEN PARTITIONING![/COLOR][/SIZE]**

---

### Post by Kira_Belka on 2011-07-24
> **mattdee132 said:**
> When I installed Ubuntu, I dual booted with Windows, but now I want to get rid of my Windows partition and only use Ubuntu.  There are no important files on the Windows partition, so I am just looking to delete it and then expand the Ubuntu partition to fill that space.  How does one go about doing that?

my hard drive looks like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3            1918       26023   193623018    7  HPFS/NTFS
/dev/sda4           26023       38914   103546881    5  Extended
/dev/sda5           26023       38658   101490688   83  Linux
/dev/sda6           38658       38914     2055168   82  Linux swap / Solaris

Hi.. if you 'll no sure in your possibilities .. just use any Ubuntu Live CD and gparted.. so it's very easy!

---

### Post by mattdee132 on 2011-07-24
> **Kira_Belka said:**
> Hi.. if you 'll no sure in your possibilities .. just use any Ubuntu Live CD and gparted.. so it's very easy!

Just looked that up and it doesnt seem to hard.  Is there any danger in resizing/moving the partition that it boots from (the main one)?

---

### Post by Quackers on 2011-07-25
There is always a small risk when moving a boot partition (as gparted will tell you if you try it). I have done it many times without a problem, but I've also had to re-install grub when things didn't go quite as planned. It's usually fixable even when things go slightly wrong, but there is a risk.
Backup everything you need before you try it!

---

### Post by egalvan on 2011-07-25
The *easiest* way to **use** the space that XP was on...


boot from a LiveCD,
run gedit.
make sure the ntfs drive is un-mounted.
tell gedit to format it as ext4 (or whatever Linux fs you like)
re-boot from your hd,
 and use the new space as storage...

No need to move, re-size, re-store, re-install grub, "grub-update", etc... :P

you can even do this from a running system, 
as (obviously) Linux does not depend on any NTFS drive.
unless you have it set up to auto-mount it,
in which case, just un-mount it... then proceed.


One thing to realize is that your NTFS partition is the only **PRIMARY** partition...
your Ubuntu is fully inside an **EXTENDED** partition.
this makes it a multi-step process to "grow" your Ubuntu into that space...

using it as a separate storage drive is much easier.

---

### Post by mattdee132 on 2011-07-25
wow, thanks.  Egalvan's idea worked very quickly and was super easy and seems to work just fine.  much safer than bothering with all that other stuff.  Just one last question: how do you set a drive to automount?

---

### Post by egalvan on 2011-07-25
> **mattdee132 said:**
> wow, thanks.  Egalvan's idea worked very quickly and was super easy and seems to work just fine.  much safer than bothering with all that other stuff.

I was born lazy, so I always look for the most efficient way of doing things.
And lets face it, NOT doing something is the epitome of efficiency :popcorn: 

>  Just one last question: **how do you set a drive to automount?**

post a copy of your **fstab** file... 
that will let us see how it's mounting currently.

---

### Post by egalvan on 2011-07-25
Also, bohdi has an *excellent* tutorial on fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by karlson on 2011-07-25
> **mattdee132 said:**
> When I installed Ubuntu, I dual booted with Windows, but now I want to get rid of my Windows partition and only use Ubuntu.  There are no important files on the Windows partition, so I am just looking to delete it and then expand the Ubuntu partition to fill that space.  How does one go about doing that?

my hard drive looks like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3            1918       26023   193623018    7  HPFS/NTFS
/dev/sda4           26023       38914   103546881    5  Extended
/dev/sda5           26023       38658   101490688   83  Linux
/dev/sda6           38658       38914     2055168   82  Linux swap / Solaris

Looking through the partition table I don't think you will be able to.

Reason being is that your NTFS partition is a primary partition and your Linux is located on the extended partitions, which will present a problem since you will need to basically not grow your extended partition, but actually move the partitions over.  Merging partitions into an extended one also won't work since at least one partition in the DOS table needs to be primary.

So your simplest solution would be to just create a filesystem on the existing NTFS partition and just mount it under Linux.

---

