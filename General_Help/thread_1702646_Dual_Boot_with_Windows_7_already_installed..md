---
title: "Dual Boot with Windows 7 already installed."
date: 2011-03-08
forum: General Help
---

### Post by DeathByLinux on 2011-03-08
Hey guys, 
                some of you might remember me from a few months ago; I was going to install a dual boot set up on both my brother and sister's computers. I successfully installed a dual boot set up on my brother's computer with vista (yuck) and ubuntu 10.10. 
Okay, so here's the new situation: My sister just bought an HP G62  and I told her that I would make it secure by putting Ubuntu on it, so that she doesn't need to install crap loads of computer security, because all she does is brows the net, listen to music, and watch movies.
Anyway, I don't think I tackled this issue last time, but I would like some guidance on a few things.
1) Why does the Disk Management in Windows 7 (and I think vista) only allow me to shrink the C: drive by a certain amount. Less than half, actually. 
Here are the numbers:
(C: )449.25GB
HP_Tools 99mb
Recovery (D: ) 16.21GB
System 199MB

(C: ) Total size shrink in MB: 460036
Size of available shrink space in MB: 217519

Do I have an exaggerated sense of entitlement here, or is this thing wrongfully telling me that I can only shrink my C: by an arbitrary number? I know that my sister will choose Ubuntu over Windows 7, so I want to give it all the space that I can, and this thing is telling me that I can only allot 210 gigs? Ridiculous!

---

### Post by DeathByLinux on 2011-03-09
No ideas? :(

---

### Post by Hedgehog1 on 2011-03-09
> **DeathByLinux said:**
> 
1) Why does the Disk Management in Windows 7 (and I think vista) only allow me to shrink the C: drive by a certain amount. Less than half, actually. 


This is a valid question.  The reason is that windows is using the partition when it is running shrink, and it will allow you to shrink down until you reach a non-movable file.  Typically the file is the windows swap file (C:/pagefile.sys).

For better or worse, that is what is happening.

To get past it, you can do this:

1) Shrink the Windows partition as much as Windows allows.
2) Defrag the Windows partition.
**3) Defrag the Windows partition again (really)**
4) Boot the Ubuntu LiveCD, select 'try', fire up gparted and shrink the Windows partition to the size you really want.
5) Reboot into windows and let it do the check disk it wants to do. It *may* reboot once after the check disk; that is OK.

Now, you are good to go and install Ubuntu in the new space.

***The Hedge***

:KS

---

### Post by mastablasta on 2011-03-09
In my country those computers come OpenSUSE preloaded. too bad she din't get one of those...
 
i think page file can also be disabled temporarily. not sure exactly how it's done in win7. you should consult the manual or call free MS support. i know it's possible to do it in WinXP. It can also be moved to another partition or disk drive.

---

### Post by DeathByLinux on 2011-03-09
> **Hedgehog1 said:**
> This is a valid question.  The reason is that windows is using the partition when it is running shrink, and it will allow you to shrink down until you reach a non-movable file.  Typically the file is the windows swap file (C:/pagefile.sys).

For better or worse, that is what is happening.

To get past it, you can do this:

1) Shrink the Windows partition as much as Windows allows.
2) Defrag the Windows partition.
**3) Defrag the Windows partition again (really)**
4) Boot the Ubuntu LiveCD, select 'try', fire up gparted and shrink the Windows partition to the size you really want.
5) Reboot into windows and let it do the check disk it wants to do. It *may* reboot once after the check disk; that is OK.

Now, you are good to go and install Ubuntu in the new space.

***The Hedge***

:KS
Okay, I am going to try this.
I have a question, though: 
Although I haven't tried this with Unix, wouldn't it be harder, since NFTS stores data one by one, whereas Unix places it all over the place to avoid fragmentation?

---

### Post by Hedgehog1 on 2011-03-09
> **DeathByLinux said:**
> Okay, I am going to try this.
I have a question, though: 
Although I haven't tried this with Unix, wouldn't it be harder, since NFTS stores data one by one, whereas Unix places it all over the place to avoid fragmentation?

DeathByLinux,

By running the defrag twice using the MS tool, gparted has the least possible amount of work to do in the NTFS partition.  Gparted is running in NTFS mode while shrinking the NTFS partition, and it is slower than a native MS program in an NTFS partition.

But it still goes pretty quick as long and you have defragged the NTFS partition first.

***The Hedge***

:KS

---

### Post by watupgroupie on 2011-03-09
I think you can probably skip the shrinking of the Windows partition inside of Windows. Just defrag it a few times and then go into gparted on a livecd and start partitioning. I've actually never defragged before partitioning in gparted. It has never taken me over half an hour to partition either.

---

### Post by Hedgehog1 on 2011-03-10
> **watupgroupie said:**
> I've actually never defragged before partitioning in gparted. It has never taken me over half an hour to partition either.

watupgroupie,

_Please don't encourage this._  Many folks think gparted is hung when it runs that long, they reboot, and then have a damaged/useless windows partition.  I have helped them clean up the mess afterwards.

Also, if you run defrag before you shrink in gparted, your run time doing a shrink in gparted is typically a minute or two.

The goal here is do do no harm.

***The (stern) Hedge***

p.s. The shrink in windows is indeed optional, but it is a leaning experience.

---

### Post by DeathByLinux on 2011-03-10
Umm... so I defragged and everything and am in ubuntu live usb boot, and booted up the gparted and am looking at the windows partition, but can't resize it, because there is a lock on it.... 
Don't know how to get around this.

---

### Post by Mark Phelps on 2011-03-10
While some folks have been able to use GParted to shrink their Win7 OS partitions without problems, others have been left with a corrupted OS partition and an unbootable PC.

Problem is, in advance, it's impossible to tell which of these will be your result.

BEST course of action, the one with the least risk, is NOT to use GParted or any other Linux utility to shrink a Win7 OS partition.  Use the Disk Management utility instead.  If it won't shrink beyond a certain point, there is a valid reason for that -- and bypassing that by using GParted is asking for trouble.

---

### Post by DeathByLinux on 2011-03-14
This is very strange. Okay, get this: I decided to just install linux on the amount of space that windows allotted me, and then I go to the installation for Ubuntu, and the space that windows allotted me is "unusable."
Wow, this is more difficult than the time I tried to do this with the vista install.

---

### Post by colinwhipple on 2011-05-21
> **DeathByLinux said:**
> This is very strange. Okay, get this: I decided to just install linux on the amount of space that windows allotted me, and then I go to the installation for Ubuntu, and the space that windows allotted me is "unusable."
Wow, this is more difficult than the time I tried to do this with the vista install.

I have the problem of the available space being marked "unusable" too.  Is there a solution?

Colin

---

