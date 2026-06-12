---
title: "Stuck on install screen :Allocate Drive Space"
date: 2011-06-25
forum: General Help
---

### Post by trebz32 on 2011-06-25
Hello,
I'm trying to install Ubuntu 11.04 alongside winXP but seem to be stuck in the Allocate Drive Space Screen. I'm afraid to change anything leading to losing my other data in winXP. I have tried installing from windows from cd but I kept getting an error. I have about 31gb free on my hard drive and I want to use about 12-15gb for ubuntu install. Can anyone assist me from this point on? Do I need to select create a new partition? Any help would be appreciated.

---

### Post by trebz32 on 2011-06-25
I have enclosed a screen shot at the point I'm stuck in

---

### Post by Quackers on 2011-06-25
Welcome to UF :-)

Your hard drive is filled with partitions. It doesn't matter that those partitions may not be fully used up, just that they are using all the disc space.
I would suggest that you defragment, then shrink your XP partition (in Windows). This will then leave some unallocated space for Ubuntu to install into.
When that is done, you should reboot Windows a couple of times top make sure it is still happy :-)
This may fix the problem.

---

### Post by trebz32 on 2011-06-25
Thanks for the reply. I forgot to mention that I first tried ubuntu 10.04LTS with an install of 7gb from within windows. I uninstalled it for more drive space because I wanted to try 11.04 but needed to upgrade to 10.10 and needed about 700mb for this upgrade and would have needed an additional 700Mb to upgrade to 11.04 which would have left my free space to about 1.gb on the ubuntu drive. What puzzles me is that the 10.04 install was much easier to select the amt of drive space a user wanted as opposed to this installation. The install steps and screenshots from the website seem different from what I'm getting and I followed all directions.

---

### Post by jramshu on 2011-06-25
The difference is you are trying to install it directly to the hdd and not into windows as before. So you are going to have to "shrink" the windows partition down and free up actual hard drive space instead of just space on a windows drive. You need to really read up on shrinking a xp partition correctly using a good partition manager. It's not hard to mess it up since xp doesn't allow for shrinking the drive the same way vista and 7 do.

---

### Post by Quackers on 2011-06-25
A wubi installation is very different from a full install to a partition.
In wubi you are using a part of your C: drive to install Ubuntu to.
In a full installation you need to create a separate partition (or at least make the space for one) to install Ubuntu into.

When partitioning a mbr partitioned disc (as yours is likely to be) you cannot exceed 4 primary partitions. Care must be taken to avoid that.

---

### Post by nzjethro on 2011-06-25
As always, make sure all of your important data is backed up. I cooked a Windows 7 install (through my own stupidity) when I was installing Ubuntu.  D'oh!

You should be able to download and burn a GParted Live CD, and then you can use that to shrink your Windows partition to create space for Ubuntu. Make sure you defragment your XP drive a couple of times before you shrink the volume, as this can free up a lot of space (especially if it's an older install). For Ubuntu, you ideally want at least 20GB or so, so make sure you can free up at least that much space when you shrink XP.

---

### Post by trebz32 on 2011-06-27
Thanks for all the info guys. I went back to the wubi install with success as I'm still testing Ubuntu for now, in the mean time I'm freeing up space and backing up important files before I begin to mess around with the XP partition. That sounds like a good idea nzetrho I will do that, thanks.

---

