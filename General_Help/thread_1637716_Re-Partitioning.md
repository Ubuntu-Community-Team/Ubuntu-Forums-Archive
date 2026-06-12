---
title: "Re-Partitioning"
date: 2010-12-04
forum: General Help
---

### Post by drazelian on 2010-12-04
A few day Ago I wiped my 250 gig hard drive. I installed win7 on it, then booted into ubuntu live, installed ubuntu side by side, and gave it 50 gigs. Today I realized that i want to give most of that space to ubuntu today because I like it more then win 7.  If i were to boot into gparted, shrink the windows partition to 50 gis, then grow my ubuntu partition to 200 gigs, would that leave both operating sytems intact? I'm trying not to corrupt anything and have to reinstall both OS's. 

Previously when i changed a partition with windows on it, then it wouldnt boot. And if I reinstall windows, it erases grub, so If I want to have both OS's work, I have to erase both, and install windows first.

Would be changing the partition sizes safe?

Thanks.

---

### Post by drazelian on 2010-12-04
bump

---

### Post by matt_symes on 2010-12-04
Hi

> Would be changing the partition sizes safe?It should be (never guaranteed though). My advice would be to defragment the hard drive if it needs it and use the windows tool to shrink the windows partition. Then use gparted to expand the ubuntu partition from the LiveCD.

Very quick bump BTW. The general advice is to leave it 24 hours before bumping.

Kind regards

---

### Post by wilee-nilee on 2010-12-04
> **drazelian said:**
> bump

First bumping is a 24 hr wait period.

Okay yes you can shrink W7 but I doubt if you will get to 50 Gigs with it's partition manager.

You realy should just fresh install all of it to be honest, make a ntfs partition for W7 the size you want with gparted, from a live cd. Then install W7 to that then install the rest in whats left, use a extended partition with the Linux.

These are both fresh installs, you can reach your goals, but it is in geekdom land my friend and getting a straight and done finish by just moving things around will take much longer the just installing it the way you want it now.

---

### Post by drazelian on 2010-12-04
Thanks for the advice.
Sorry about the bump, I'm new on the forums and I don't know all the etiquette yet.
I'll keep that in mind next time.

---

### Post by Quackers on 2010-12-04
If you are resizing a Windows 7 partition it is usually safer to use the Windows Disk Management console (Start > right-click Computer > Manage > Disk Management > right click on the drive you want to shrink and select shrink). 
It is also recommended to defrag the drive at least once beforehand.
It is also good practise to reboot into Windows a couple of times to make sure everything is ok and no chkdsk is required.
When all that's done I would recommend resizing the Ubuntu partition by using the Ubuntu live cd version of Gparted (as that way no system partitions are mounted).
Please bear in mind that you can only extend a partition into unallocated space that it is next to.

---

### Post by wilee-nilee on 2010-12-04
> **drazelian said:**
> Thanks for the advice.
Sorry about the bump, I'm new on the forums and I don't know all the etiquette yet.
I'll keep that in mind next time.

I don't care but if done enough you will get some response from the mods, but they are actually quite fair. ;) Does the reinstall schema work for you.

I only suggest this as it is so fresh that there must not be much there to back up.

---

### Post by drazelian on 2010-12-04
Well, I just tried booting into win7 for the first time since installing ubuntu. It didnt actually work. I guess I don't even want it that much, and WINE can emulate the programs that I do need, so I'm just going to delete the windows partition and give all the 200gb to ubuntu. 

Should I do this with gparted livecd or gparted under the ubuntu live cd?

---

### Post by Quackers on 2010-12-04
Either should be ok.
While you are in Gparted please take note of whether your /root partition (for Ubuntu) is a primary partition or not, and whether there is a boot flag set on it. Some bioses need a boot flag to boot (although Linux doesn't)

---

### Post by drazelian on 2010-12-04
windows 7 is the primary partition. If I delete that, then put a boot flag on Ubuntu, all should be good right?

---

