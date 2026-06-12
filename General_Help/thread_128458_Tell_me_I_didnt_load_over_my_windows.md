---
title: "Tell me I didnt load over my windows"
date: 2006-02-11
forum: General Help
---

### Post by abelethan on 2006-02-11
I set up a dual boot system for windows and ubuntu. Ubuntu was a 35G partition and Windows the remaining. For some reason I was having problems with Ubuntu so I reinstalled it. Before this I could jump between the two (windows/ubuntu) without a problem. When I reinstlled my windows boot disappared. I thought I selected the old ubuntu partition when I reinstalled but now it get this when I do a fdisk


Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        4083    32764567+  83  Linux
/dev/hda3            4261        9538    42395535   83  Linux
/dev/hda4            4084        4260     1421752+   5  Extended
/dev/hda5            4084        4260     1421721   82  Linux swap / Solaris

Partition table entries are not in disk order

Can anyone tell me I didnt and how to get it back. Or whos going to be the one to break my spirt. Cause all my windows data wasnt backed up :(

---

### Post by aysiu on 2006-02-11
You over-wrote your Windows partition accidentally.
There's no way to recover the lost data.
This is why people always encourage you to back up before doing anything serious (repartitioning, reinstalling).

---

### Post by crypticreign on 2006-02-11
[QUOTE=aysiu]You over-wrote your Windows partition accidentally.
There's no way to recover the lost data.
This is why people always encourage you to back up before doing anything serious (repartitioning, reinstalling).[/QUOTE]

Ouch!  Indeed it's gone.  

:(

---

### Post by steve.horsley on 2006-02-11
It's a dirty job, but somebody has got to do it.

You say you had 35G Ubuntu and rest windows. Well, I can't see 35G, but I can see a 32G and a 42G, both Linux, and no NTFS. You can find out which one Ubuntu is running on with the console command **df -h**. My guess is that hda2 used to be windows because it's still marked as bootable. If Ubuntu has its / mounted on hda2 than your windows stuff has definitely gone.

There is a very remote chance that ubuntu is installed on hda3, and if this is the case, there is a very remote chance that the windows stuff is still there on hda2, but the partition has been marked as type Linux without having been formatted. In this unlikely case, you may be able to recover windows by using the command **sudo fdisk /dev/hda** and setting the type back to NTFS. Be careful with fdisk, and come back for help if in doubt.

Sorry to be pessimistic, but I guess 90% probability it's gone.

---

### Post by abelethan on 2006-02-11
[QUOTE=steve.horsley]It's a dirty job, but somebody has got to do it.

You say you had 35G Ubuntu and rest windows. Well, I can't see 35G, but I can see a 32G and a 42G, both Linux, and no NTFS. You can find out which one Ubuntu is running on with the console command **df -h**. My guess is that hda2 used to be windows because it's still marked as bootable. If Ubuntu has its / mounted on hda2 than your windows stuff has definitely gone.

There is a very remote chance that ubuntu is installed on hda3, and if this is the case, there is a very remote chance that the windows stuff is still there on hda2, but the partition has been marked as type Linux without having been formatted. In this unlikely case, you may be able to recover windows by using the command **sudo fdisk /dev/hda** and setting the type back to NTFS. Be careful with fdisk, and come back for help if in doubt.

Sorry to be pessimistic, but I guess 90% probability it's gone.[/QUOTE]

Actually I was thinken that ubuntu was on the hda2 and windows is on the hda3. Its the one with the largest size. And thats the size windows was when I started this whole process. Ya the 35 was changed when I redid it because it took 1.5 the first time for a swap and then another 1.5 the second time for the swap. For some reason it wouldnt allow me to deleate the first 1.5 swap partition. It just no longer shows up. If you could explain how I might change the hda3 from linux to somthing like windows I would appraciate it. If its gone then its gone. I am not afraid of ruining anything now. Since I am already under the impression I did ruin it :). I appraciate your help

---

