---
title: "bsod after gparted used"
date: 2010-03-29
forum: General Help
---

### Post by prattage723 on 2010-03-29
I have a dual boot of Ubuntu9.10 and XP. For some reason XP wouldnt show me how big my HD was, only said about 130 gigs, when in reality its a 1TB drive. So I installed XP on the drive that said 130 gigs. Then installed Ubuntu and went GParted and resized the XP partition to about 460 gigs (about half my drive). Now I get a BSOD and im assuming its because I resized the partition. Does anybody know of a way to resolve this issue?

Any help would be appreciated thank you.

---

### Post by Notebooks on 2010-03-29
Had this happen to me once. I ended up having to reinstall windows. BUT, the next few times I had to resize, I defragmented first and GParted worked just fine. I don't know why.

---

### Post by prattage723 on 2010-03-29
I would just reinstall windows. But for some reason my windows cd doesnt read my drive right and only sees 130 gigs. It doesn't see the Ubuntu partition either so it deletes it when it installs.

---

### Post by t0p on 2010-03-29
As you have been resizing partitions and installing operating systems, I'm going to hazard a guess that don't have any files on the disk that you need to retrieve.  So my suggestion is you start over.

Use gparted to partition your drive the way you want it.  Then, when you have the drive partitioned, install XP on one partition and Ubuntu on another.  Don't do any resizing after you've installed anything - get the sizes right first, *then* install the operating systems.

---

### Post by prattage723 on 2010-03-29
> **t0p said:**
> As you have been resizing partitions and installing operating systems, I'm going to hazard a guess that don't have any files on the disk that you need to retrieve.  So my suggestion is you start over.

Use gparted to partition your drive the way you want it.  Then, when you have the drive partitioned, install XP on one partition and Ubuntu on another.  Don't do any resizing after you've installed anything - get the sizes right first, *then* install the operating systems.


That seems like the logical thing to do. But When I boot from the windows cd it only reads 130 gigs. I think that I should take the windows half of the drive and partition into 4 smaller partitions, under 130 gigs. and that might work. I dont know

---

### Post by Notebooks on 2010-03-29
> **prattage723 said:**
> That seems like the logical thing to do. But When I boot from the windows cd it only reads 130 gigs. I think that I should take the windows half of the drive and partition into 4 smaller partitions, under 130 gigs. and that might work. I dont know
Hmm... sounds like an LBA problem (speculation). This may be Windows disliking your disk controller. What's your disk setup? (hardware)

---

### Post by waynefoutz on 2010-03-29
This happened to me once. I ended up reinstalling the Windows as well. When you resize a Windows partition, Windows doesn't much like it. It wants to scan the drive for errors. I found out the hard way if you hit the escape button to skip that checkdisk, then you just hosed your windows install. 

After you reinstall Windows, you are going to lose your Grub menu and access to Ubuntu. Follow this guide to get Grub back so you won't have to reinstall Ubuntu as well.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

---

### Post by prattage723 on 2010-03-29
> **Notebooks said:**
> Hmm... sounds like an LBA problem (speculation). This may be Windows disliking your disk controller. What's your disk setup? (hardware)


I have a 1tb seagate drive in the first SATA slot and a 80gig western digital drive in the third SATA slot

I just partitioned my drive into 4 different partitions. And the windows cd still only shows one partition "c: partition1 (unknown) 131024 mb" something like that.. not the exact mb number but close. But thats the only partition it shows for the 1TB drive, and it is partitioned into 4 partitons now. So lost at this point. How do I get windows cd to read the drive correctly?

---

### Post by waynefoutz on 2010-03-29
Windows can't see ext* partitions. The one that is formatted in NTFS is the one you want to reinstall Windows on. Needless to say, but I will anyway, make sure you have any critical data in your Linux partitions backed up. When you're done, use the guide I posted earlier to restore GRUB so you can dual boot again.

---

### Post by prattage723 on 2010-03-29
Okay I figured out what was wrong. Service Pack 1 for XP can only handle disks up to 131 gigs. So i just need to find a windows install cd with SP2 on it, Which I have found at a friends house. Going to go pick it up on wednesday. But thats the reason I cant install, Is because I have too big a drive

Unless anybody knows of a way I can get an ISO and run it from ubuntu, I'm stuck with just ubuntu and no games till wednesday.

---

