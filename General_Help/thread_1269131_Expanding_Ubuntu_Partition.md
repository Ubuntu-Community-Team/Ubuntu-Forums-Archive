---
title: "Expanding Ubuntu Partition"
date: 2009-09-17
forum: General Help
---

### Post by Mercenary(FH) on 2009-09-17
A Little subknowledge. i have a dual boot computer. half windows vista buisness 64bit (ewww) and half ubuntu 9.04 which i installed using "Wubi".

the original partition size I chose for ubuntu was something like 18gigs.

but now I kinda wanna make it my main desktop (only  going back to windows to play a few games)

Is there any way to expand JUST the ubuntu partition without messing up my windows or ubuntu installation.?

or having to reinstall.

thx :):confused:

---

### Post by Partyboi2 on 2009-09-18
Hi, you should be able to use [[COLOR=Blue]LVPM[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")  to migrate your wubi install to a real partition.

---

### Post by Mercenary(FH) on 2009-09-18
any risk losing data in doing this?

---

### Post by Zoot7 on 2009-09-18
Here's what I'd do.

Defrag the Windows partition a few times, then either boot off the Ubuntu liveCD or the Gparted liveCD and shrink the NTFS partition to whatever size you want to shrink it to. Then resize your Ubuntu partition to your desired size too.

Now, due to the fact that Microsoft are great and really care about their customers and make it extremely easy for people especially when they want to do things such as dual boot, :p Vista won't boot.
If you partition the hard drive with anything else except the Vista partitioner (which is really really crap) it won't boot.

Now the thing to do is boot off your Vista setup CD and use that to write the Vista bootloader back to the MBR so that Vista boots okay.
Now Ubuntu won't boot, but simply boot off the liveCD and run the following from a terminal.
```
sudo grub
find /boot/grub/stage1
```

That'll return something along the lines of (hd0,1).
Then do
```
root (hd0,1) - or whatever that last command returned.
```
and finally
```
setup (hd0)
```

It's a bit of a roundabout method, but I've done it in the past and it's worked okay for me. It's also annoying, considering the source of all the hassle is Vista, all XP would look for you to do is run chdsk upon booting.
As for data loss, it's always a risk when partitioning your hard drive, so back up the essentials, also be sure to defrag the NTFS partition a few times otherwise it'll take a very long time resize.

***EDIT***
I'm just after reading your post properly and it's Wubi you're talking about. Never used it so I've no idea.
Sorry, stupid me. :p

---

### Post by Partyboi2 on 2009-09-18
> **Mercenary(FH) said:**
> any risk losing data in doing this?
There is always a small risk of losing data when working with partitions. Backup your important stuff before working on partitions.

---

### Post by Mercenary(FH) on 2009-09-19
Keep in mind I want to keep my Vista partition. but just make my ubuntu partition bigger?

and is installing via wubi.....like not a real.....Partition or wut?

---

### Post by Partyboi2 on 2009-09-19
Installing using wubi, installs Ubuntu to the same partition as your Windows using a virtual disk.  You can either use LVPM to increase the size of your Ubuntu virtual disk, or you can use it to move your Ubuntu install to its own dedicated partition. One of the advantage of moving to a dedicated partition is if your Vista crashes or needs to be reinstalled you don't have to worry about losing Ubuntu. You may also notice better performance with Ubuntu running from its own partition. 
Moving Ubuntu to its own dedicated partition will not remove Vista.

---

