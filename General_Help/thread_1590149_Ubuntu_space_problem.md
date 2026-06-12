---
title: "Ubuntu space problem"
date: 2010-10-07
forum: General Help
---

### Post by Dxlnc on 2010-10-07
Hello mates!

   I was silly enough to install Linux - Ubuntu  after having Windows vista on, and now that I've started downloading a lot of things space is getting short in Ubuntu. 

   I'm wondering if there is any way to shorten the space what Windows is taking and transfer it to Ubuntu without having to reinstall everything which would make things a pain in the *** on several levels. Thank you!:-)

   - Dxlnc

---

### Post by coffeecat on 2010-10-07
First thing - do you have a Wubi install or did you install Ubuntu to its own partition(s)?

If you have a conventional (non-Wubi) dual-boot install, you might be able to shrink the Windows C: partition and enlarge the Ubuntu one depending on what your partition layout is like. One caveat - you must use Vista's own utility to shrink the C: drive.

If you are non-wubi, open a terminal and post the output of:

```
sudo fdisk -lu
```

---

### Post by Dxlnc on 2010-10-07
> **coffeecat said:**
> First thing - do you have a Wubi install or did you install Ubuntu to its own partition(s)?

If you have a conventional (non-Wubi) dual-boot install, you might be able to shrink the Windows C: partition and enlarge the Ubuntu one depending on what your partition layout is like. One caveat - you must use Vista's own utility to shrink the C: drive.

If you are non-wubi, open a terminal and post the output of:

```
sudo fdisk -lu
```


   I have no clue what (non-Wubi) it is, and I did the dual boot with an Ubuntu CD which does it automatically so I don't think I have Wubi. 

   This is what I got when I ran your command:

   Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   605565231   302782584+   7  HPFS/NTFS
/dev/sda2       605566974   976773119   185603073    5  Extended
/dev/sda5       605566976   964696063   179564544   83  Linux
/dev/sda6       964698112   976773119     6037504   82  Linux swap / Solaris

---

### Post by oldfred on 2010-10-07
If I am reading that correctly, you seem to have a good sized linux partition.

Run this:

df -Th

---

### Post by Dxlnc on 2010-10-07
Yeah, 170 GB on the Ubuntu partition, but I've downloaded a lot of stuff lately, and I use Ubuntu mostly so I'd like to move another 100 to Ubuntu from Windows. 

The command landed me with:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4    169G  161G     0 100% /
none      devtmpfs   1003M  292K 1003M   1% /dev
none         tmpfs   1007M  2.8M 1004M   1% /dev/shm
none         tmpfs   1007M  100K 1007M   1% /var/run
none         tmpfs   1007M     0 1007M   0% /var/lock
none         tmpfs   1007M     0 1007M   0% /lib/init/rw

Appreciate the help by the way:-)

---

### Post by oldfred on 2010-10-07
You must have copied a ton of stuff into /home. I have installed many programs and have used only 6GB for my system partition and when I had a separate /home it was less than 1GB as I had moved all data to a data partition.

I prefer keeping systems, both windows & Ubuntu separate from data. Either separate /home or my preference a separate data partition. I prefer a separate /data partition as I install several versions of Ubuntu and want the same data in all of them. If just upgradeing then a /home is fine. I also have a /shared NTFS partition for any data that I want in windows and Ubuntu.

The only issue of shrinking your windows partition is that you will have to move your Ubuntu partition left which means it will have to copy & verify all data (very slow & a little more risk). All partition changes have some risk so you must have good backups.  You probably then have to reinstall grub. UUID should not change but may and then you have to edit fstab with new UUID.

An alternative is just shrink windows and make a data partition. You do not have to have all data in one partition. You then can mount that in fstab into your /home or mount and link into /home so it looks just like a folder in /home.

---

### Post by coffeecat on 2010-10-07
> **Dxlnc said:**
> I have no clue what (non-Wubi) it is, and I did the dual boot with an Ubuntu CD which does it automatically so I don't think I have Wubi. 

Indeed, you do not have Wubi - which is just as well. :) Wubi:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I have nothing to add to oldfred's excellent advice. And I agree with what he says about how you must have filled up a 170GB Ubuntu partition. I have systems rattling around inside 15GB partitions with plenty of room to spare and with my data separate. How many movies have you got there? When do you find time to watch them all? :wink:

When you've decided what you want to do, post back if you need any more help.

---

### Post by Dxlnc on 2010-10-15
Well, I got like 40 movies and loads of series that take up 99 GB space;-) 
Thanks for comment though!

---

### Post by Dxlnc on 2010-10-15
All I can say is thanks a million:-)

---

