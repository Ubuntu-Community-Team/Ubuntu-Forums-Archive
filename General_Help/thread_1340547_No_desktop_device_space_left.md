---
title: "No desktop device space left"
date: 2009-11-28
forum: General Help
---

### Post by DarkSunrize on 2009-11-28
Hello I'm brand new to linux. My mom's computer kept crashing with windows so i asked her and she let me install ubuntu 9.04 on her laptop. It has been running great except that now on my desktop i have nothing on there but it says i have 0 bytes free and it will not let me add or download anything to my desktop. I deleted my trash and still nothing... can anyone help me free up my desktop for use??

---

### Post by jollysnowman on 2009-11-28
I'm confused... does your desktop have 9.04? What does this have to do with your mom's laptop?

Also:
-how big is your hard drive?
-how do you have it partitioned?
-how much free space did you have before you installed (to whatever computer you're talking about, b/c I have no idea)?

---

### Post by SuaSwe on 2009-11-28
I'm guessing you're referring to the Desktop folder (/home/user/Desktop) on the laptop.

Could you post the output of the following command:

```

sudo fdisk -l

```

? 

Cheers!

---

### Post by DarkSunrize on 2009-11-28
250 gig hard drive. The thing about it being my mom's computer was just background information, idk how big my partition is, i just let it partition itself i didnt change any settings (is there any way for me to tell?) and i had like 200 gigs of free space b4 i installed

---

### Post by DarkSunrize on 2009-11-28
> **SuaSwe said:**
> I'm guessing you're referring to the Desktop folder (/home/user/Desktop) on the laptop.

Could you post the output of the following command:

```

sudo fdisk -l

```? 

Cheers!


Here is the output


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bf49399

   Device Boot  :    Start :        End :     Blocks :  Id : System
/dev/sda1   *          : 1      : 29211  : 234637326   : 7 : HPFS/NTFS
/dev/sda2          : 29538     :  30401    : 6940080   : 7 : HPFS/NTFS
/dev/sda3          : 29212      : 29537    : 2618595   : 5 : Extended
/dev/sda5          : 29212      : 29515    : 2441848+ : 83  Linux
/dev/sda6          : 29516      : 29537     : 176683+ : 82 : Linux swap / Solaris

Partition table entries are not in disk order

i added in the semi colons to help seperate the columns because this is auto aligning everything

---

### Post by SuaSwe on 2009-11-28
WTF, sorry, am being a div!

I meant this command:

```

df

```

Sorry!

---

### Post by sobol_rz on 2009-11-28
> **SuaSwe said:**
> WTF, sorry, am being a div!

I meant this command:

```

df

```Sorry!

maybe 
```

df -h

```:)

---

### Post by DarkSunrize on 2009-11-28
> **SuaSwe said:**
> WTF, sorry, am being a div!

I meant this command:

```

df

```Sorry!


output for df


Filesystem          : 1K-blocks     : Used Available Use% Mounted on
/dev/sda5             : 2403420  : 2281632        : 0 100% /
tmpfs                  : 472964        : 0   : 472964  : 0% /lib/init/rw
varrun                 : 472964      : 108   : 472856  : 1% /var/run
varlock                : 472964       :  0   : 472964  : 0% /var/lock
udev                   : 472964      : 148   : 472816  : 1% /dev
tmpfs                  : 472964     : 1132   : 471832  : 1% /dev/shm
lrm                    : 472964     : 2760   : 470204  : 1% /lib/modules/2.6.28-11-generic/volatile
overflow                 : 1024      : 364      : 660 : 36% /tmp
/dev/sda1           : 234637320 : 23913900 : 210723420 : 11% /media/disk

semi colons help make more readable

---

### Post by SuaSwe on 2009-11-28
/dev/sda5 : 2403420 : 2281632 : 0 100% /

^ You're using 100% of this partition. Do you know what you have on there?

---

### Post by DarkSunrize on 2009-11-28
No i do not? Hahaha srry i feel like a major noob asking for help with this

---

### Post by SuaSwe on 2009-11-28
I do actually, I realise (man, my brain is really not with it today!).

Your root partition is full, basically. You should be able to extend it I think, although I daren't advise how! Lemme have a look round for you.

---

### Post by DarkSunrize on 2009-11-28
ok thank u soooo much!!! :)

---

### Post by SuaSwe on 2009-11-28
[http://ubuntuforums.org/showthread.php?t=336386](http://ubuntuforums.org/showthread.php?t=336386)

Proceed with caution though, these things can really mess up your system! Might be best to wait from further advice before doing anything with it. ;)

---

### Post by DarkSunrize on 2009-11-28
haha thank u. Actually i read that i can just remove ubuntu and re-install and increase the partition size.... what do u think?

---

### Post by SuaSwe on 2009-11-28
Yep, if you're happy doing that!

I'd give like 10-20GB for / (root), 1GB or so for swap, and the rest for /home/ (if this is how you want it partitioned, obviously!).

---

### Post by DarkSunrize on 2009-11-28
haha thank u! Do u know how i go about removing this copy of ubuntu to reinstall a new one?

---

### Post by SuaSwe on 2009-11-28
Yeah: download a LiveCD (I'm going after the sequence of the Intrepid disk as that's the one I've always used) and boot from it, and select 'Install Ubuntu' once you arrive at the menu. You'll get into a graphical environment where you can select Install - it'll give you some regional & language options, and once you've selected them you will get to the partition manager.

In there, you want to select 'Manual', then select the drive you want to install on; select Edit Partition Table and add each partition one by one by selecting the file system, ticking 'format'*, selecting the size and finally the mount point (the way I do it is "/", "swap" and "/home/") for each one.

These instructions aren't verbatim by the way, as I don't have it in front of me - also Jaunty and Karmic LiveCD's may look different from this!


*The swap partition will not require formatting - oh, and note that by formatting you'll lose ALL data!

---

### Post by DarkSunrize on 2009-11-28
well i downloaded a live CD to install linux on this laptop. This thing couldnt keep windows open long enough so i made the live CD on my dad's computer. Can i just pop the CD in the drive and run it here in ubuntu and overwrite the current partition and make it bigger?

---

### Post by SuaSwe on 2009-11-28
Yeah, I should think so - try booting into a live environment and running the partition manager (you may have to install it by running 'sudo aptitude install gparted' in Terminal, although if you select Install it will already be in there) - you'll be able to see all your partitions once in there, then you can choose what looks easiest. :) I'd probably format and reinstall the whole thing though if I were you, as long as you don't have any data on there that you need to keep!

---

### Post by DarkSunrize on 2009-11-28
wait a second.... I found a program in the add and remove applications called GNOME partition editor... can i use this and just make the partition larger?

---

### Post by SuaSwe on 2009-11-28
I could be wrong but I don't think it's possible (or advisable) to resize a mounted partition - in other words, you want to be in something like a LiveCD so that root isn't mounted when you're working on it.

---

### Post by DarkSunrize on 2009-11-28
haha srry but what does mounted mean?

---

### Post by 3rdalbum on 2009-11-28
Ubuntu doesn't "partition itself" - how would it know what amount of space to give? You just chose "resize partition" without moving the little slider to say how much space you wanted Ubuntu to have... ...as a result, Ubuntu has installed with the safest default settings, which is the bare minimum necessary to boot up the system.

This is a common problem for newbies, and now the 9.10 installer warns you if you try to use the default setting.

You will need to boot up the Ubuntu 9.04 Desktop CD in "Try Ubuntu" mode, and use the Partition Editor program (System > Administration > Partition Editor) to resize the Windows partition downwards, and upsize the Ubuntu partition.

EDIT: I just found a HOWTO for you: [http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

Make sure you have a backup of everything important before you mess with partitioning.

---

### Post by 3rdalbum on 2009-11-28
> **DarkSunrize said:**
> haha srry but what does mounted mean?

Your mechanic doesn't work on your car's engine while driving it down the road; you can't modify a partition that's in use on your computer. Resize the partition from a live CD (the Ubuntu Desktop CD).

If a disk or partition is "mounted", it has been made available for the operating system and programs to access. The process of doing this is called "mounting", and the reverse is "unmounting".

---

### Post by SuaSwe on 2009-11-28
When a disk/drive/partition is mounted, it means it's accessible to the computer (and probably in use in some way). When booting from a LiveCD, the PC is running off it instead of the root partition on your hard drive and you can therefore resize it safely.

---

