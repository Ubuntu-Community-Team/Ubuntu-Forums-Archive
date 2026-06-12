---
title: "Ubuntu 11.10 Partitioning?"
date: 2011-10-20
forum: General Help
---

### Post by Snowboi on 2011-10-20
Hey there
today i was planning on installing ubuntu 11.10 and did some research on how to partition...
I still appear to be having trouble understanding how exactly to partition and have searched for other topics similar to this and none appear to help me
I wanna install ubuntu 11.10 with about 60gb alongside with windows 7 and i do not want to use wubi

Computer Info
Thinkpad t520(s)
4gb ram

Here are my partition tables i took a screenshot during installation

---

### Post by irv on 2011-10-20
It looks like your sda3 is the biggest partition and the one that has the least data on. make sure you backup you files on that partition and then boot with the live cd. Go to gparted and resize that partition so you have the 60 gig you want. apply the changes and then reboot. 

When you got to install use this space to install Ubuntu. If you have any other question before installing post them here.

---

### Post by Snowboi on 2011-10-20
> **irv said:**
> It looks like your sda3 is the biggest partition and the one that has the least data on. make sure you backup you files on that partition and then boot with the live cd. Go to gparted and resize that partition so you have the 60 gig you want. apply the changes and then reboot. 

When you got to install use this space to install Ubuntu. If you have any other question before installing post them here.

Okay, thanks how would i go about making a partition for free space?
i know i boot into the usb or live cd and open gparted but what next?

---

### Post by irv on 2011-10-20
> **Snowboi said:**
> Okay, thanks how would i go about making a partition for free space?
i know i boot into the usb or live cd and open gparted but what next?

After you resize the partition you can create a new partition, but once you reboot and start the install it should find the free space and you can use this. Remember you will want about 64 gig so you can have 60 gig for Ubuntu and 4 gig for swap. The install should take care of setting this up.

---

### Post by Snowboi on 2011-10-20
> **irv said:**
> After you resize the partition you can create a new partition, but once you reboot and start the install it should find the free space and you can use this. Remember you will want about 64 gig so you can have 60 gig for Ubuntu and 4 gig for swap. The install should take care of setting this up.


Alright so just to be sure
i select /dev/sda3 right click resize/move then put the

free space preceding to  : 65000
new size i leave alone : 155243 (at the moment)
free space following : leave alone ? (currently at 1)
all are (MiB)
and alight to MiB correct?

---

### Post by irv on 2011-10-20
> **Snowboi said:**
> Alright so just to be sure
i select /dev/sda3 right click resize/move then put the

free space preceding to  : 65000
new size i leave alone : 155243 (at the moment)
free space following : leave alone ? (currently at 1)
all are (MiB)
and alight to MiB correct?
There is 1024 MiB to a Gig so if you want 65 Gig take 1024X65= 66,560 MiB.
Sorry it took me so long to get back to you, but I was on the road and just got home.

---

### Post by Snowboi on 2011-10-20
> **irv said:**
> There is 1024 MiB to a Gig so if you want 65 Gig take 1024X65= 66,560 MiB.
Sorry it took me so long to get back to you, but I was on the road and just got home.

so i would enter that for free space preceding to?
and leave the others the way they are?

---

### Post by Snowboi on 2011-10-21
Sorry for the double post :S
but is this how it should look?
(im okay with it being 68gbs)
my only concern is to be sure i don't lose any windows data or risk corrupting my windows partition (but i do believe all system files are on the other partition

---

### Post by experience on 2011-10-21
> **Snowboi said:**
> Sorry for the double post :S
but is this how it should look?
(im okay with it being 68gbs)
my only concern is to be sure i don't lose any windows data or risk corrupting my windows partition (but i do believe all system files are on the other partition

You really should have all your files backed up, before proceeding. Though this procedure should usually be safe.

---

### Post by mastablasta on 2011-10-21
better use windows disk manager for this to create an empty disk space. some peopel had failed with gparted and win7 combo. also if you are doing changes to disk where data is located you should defragment the partition (at leats two times) first to avoid any possible loss of data.
 
otherwsie that is what you want (as shown on your picture). the os will then go into that unalocated disk space.

---

### Post by Snowboi on 2011-10-21
> **mastablasta said:**
> better use windows disk manager for this to create an empty disk space. some peopel had failed with gparted and win7 combo. also if you are doing changes to disk where data is located you should defragment the partition (at leats two times) first to avoid any possible loss of data.
 
otherwsie that is what you want (as shown on your picture). the os will then go into that unalocated disk space.

Alright, iv already backed up important files
(ill try windows disk manager)

---

