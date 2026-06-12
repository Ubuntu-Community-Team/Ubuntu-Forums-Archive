---
title: "I need help with GParted..."
date: 2011-05-19
forum: General Help
---

### Post by ChaosChris2009 on 2011-05-19
[CENTER]I have some unwanted partitions and I'd like to know how I can use GParted to move these partitions into one single partition

I'm on Natty, help is appreciated.[/CENTER]

---

### Post by wildmanne39 on 2011-05-19
> **ChaosChris2009 said:**
> [CENTER]I have some unwanted partitions and I'd like to know how I can use GParted to move these partitions into one single partition

I'm on Natty, help is appreciated.[/CENTER]
Hi, you should leave the swap file it can effect the speed of ubuntu.

---

### Post by eltommo on 2011-05-19
Ok, do you know if you are using all the ext4 partitions?
You could also delete one of the swap partitions or merge them into a larger partition. Do you know how much swap space you want?

---

### Post by ChaosChris2009 on 2011-05-19
> **eltommo said:**
> Ok, do you know if you are using all the ext4 partitions?
You could also delete one of the swap partitions or merge them into a larger partition. Do you know how much swap space you want?

Originally the other partitions were Pinguy OS that I was trying to dual boot with the other day, it didn't show up on grub and now I'm trying to get rid of the partitions to dual boot Win7 with Ubuntu.

And how would I know much swap space to give it?

---

### Post by eltommo on 2011-05-19
Oh, that's right, I remember you :D. If you want to try to get grub displaying the pinguy os, you can try
```
sudo update-grub
```in ubuntu. But otherwise if the data you want to keep is **only** on /dev/sda1 then you could turn the swap off by right clicking the active swap and pressing swap off. Then you could delete all the partitions with the exception of /dev/sda1
Then you could make 2 new partitions out of the empty space.
One would be the swap and the other would be the ntfs partition.
The recommended swap size is twice the amount of ram you have.
If you decide to repartition, make sure "primary partition" is selected for the disks you partition instead of "extended partitions." 
If you think you would like some extra space for playing around with installing more os's in the future, then leave a portion of space un-partitioned at the end.
This free space can later be formatted into an extended partition which can hold any number of sub partitions (the maximum number of primary partitions is 4)

Just remember if you do all this, all your data on all the partitions other than /dev/sda1 will be deleted.

When you install windows, it will (I'm pretty sure) write over grub with its own bootloader. Don't worry, there are plenty of guides showing how to restore grub.

---

### Post by wildmanne39 on 2011-05-19
> **ChaosChris2009 said:**
> Originally the other partitions were Pinguy OS that I was trying to dual boot with the other day, it didn't show up on grub and now I'm trying to get rid of the partitions to dual boot Win7 with Ubuntu.

And how would I know much swap space to give it?

Hi,2 gigs is big enough, as for the twice the amount of ram that applied when computers did not have much ram.

---

### Post by wildmanne39 on 2011-05-19
> **ChaosChris2009 said:**
> Originally the other partitions were Pinguy OS that I was trying to dual boot with the other day, it didn't show up on grub and now I'm trying to get rid of the partitions to dual boot Win7 with Ubuntu.

And how would I know much swap space to give it?
Hi, on installing windows it always has to be first, because it will try to take up the whole drive, maybe by partitioning first, you can select away that it will not over write ubuntu, I do not think so,if you can you will have to reinstall grub, I had to just because I used gparted to resize and move partitions.

---

### Post by eltommo on 2011-05-19
> **wildmanne39 said:**
> Hi, on installing windows it always has to be first, because it will try to take up the whole drive, maybe by partitioning first, you can select away that it will not over write ubuntu, I do not think so,if you can you will have to reinstall grub, I had to just because I used gparted to resize and move partitions.
I'm pretty sure you can select the partition to install windows on in  win 7. Having said that, I have had issues in the past, but I have got  it to work. Though it is certainly easier to install win7 before ubuntu.

---

### Post by srs5694 on 2011-05-20
> **wildmanne39 said:**
> Hi, on installing windows it always has to be first, because it will try to take up the whole drive, maybe by partitioning first, you can select away that it will not over write ubuntu, I do not think so,if you can you will have to reinstall grub, I had to just because I used gparted to resize and move partitions.

In my experience, retail versions of Windows can be restricted to install only to whatever partition(s) you select. Many OEM Windows installers (that is, the recovery discs you get with a new PC, when the vendor bothers to provide them) will only restore the computer to a "factory-fresh" condition, and will overwrite anything else you've installed.

FWIW, I'm planning to build a new multi-boot PC soon, and this behavior is one of the reasons I'm planning to build it myself rather than buy it pre-built; I don't want to be restricted by the Windows installer when I need to re-install it (as I expect to do at some point, Windows being what it is).

---

