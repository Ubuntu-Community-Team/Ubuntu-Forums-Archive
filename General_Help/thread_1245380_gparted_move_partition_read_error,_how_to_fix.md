---
title: "gparted move partition read error, how to fix?"
date: 2009-08-20
forum: General Help
---

### Post by Statik on 2009-08-20
Hi all,

I'm not familiar enough with the e2fschk command to know how to fix this, so I'm asking for a little help.

My wife's laptop has a 5gig root partition, an 89 gig home partition and a small swap partition. The root partition recently began to complain of running out of space, so I went to shrink the home partition by 5 gig and expand the root partition.

The resize operation found some errors, fixed them, and then proceeded without trouble. However, it left the 5 gig of unpartitioned space at the end of the home partition. I want to move it to the start of the extended partition ( and give it to the primary partition eventually).

When attempting to move the partition, gparted first conducts a scan of the partition using e2fschk, which succeeds, and then tries to read all of the blocks. The reading fails and thus I cannot move the partition.

How can I repair the partition so that it can be moved?

Thanks

Statik

---

### Post by Statik on 2009-08-23
*bump*

No ideas? The laptop is usable right now, but I can't do any more updates because of lack of space. Any assistance would be appreciated.

Statik

---

### Post by Statik on 2009-08-24
Wow. Everybody must be on vacation. :)
I usually see responses galore to questions like this.

Statik

---

### Post by Statik on 2009-09-11
ok, taking my life in my hands, I've booted from the live CD and am running:
```
sudo e2fsck -pcfkv /dev/sda6
```

Should this cause any trouble, or run for an excessively long time or any other such nonesense?

Statik

---

### Post by akakingess on 2009-09-11
I am not enough of an expert to help with this, but are you using Gparted for the disk reconfiguration? Just wondering, I know that would be the proper tool to repartition disks. If it's not installed it is easy enough to install (i.e.  -   " sudo apt-get install gparted" )

Edit: I was in such a hurry here at work, I didn't even notice the dang subject line, sorry about that, disregard my entire post.

---

### Post by StuartN on 2009-09-11
> **Statik said:**
> How can I repair the partition so that it can be moved?

1) The partitions you are altering must ALL be unmounted when checking and when modifying or moving. You must boot from a CD or USB memory and run parted or Gparted from the CD / USB.

2) If it is the empty 5 Gb you are trying to check or move, then you could simply delete the partition, then move the preceding partition up to the end of the disc, leaving the 5Gb before it.

3) Make a back up onto an external drive or DVD!

---

### Post by Statik on 2009-09-12
I am using gparted

I am booting from the live CD so that the HD partitions are unmounted.

The partitions are laid out like this:
```

+---------------+------------------------------------------------------+
|               | +------------------------------+         +---------+ |
|  / (5gig)     | |  home (~120gig I think)      | 5 gig   | swap    | |
|               | +------------------------------+         +---------+ |
+---------------+------------------------------------------------------+

```

The home partition used to fill the 5 gig unpartitioned space as well. GParted successfully shrank it, but it fails when moving it to the right. It is running e2fsck which hits and error and aborts. I am trying to find a way to fix that error so that I can rerun gparted and move the partition over, shrink the extended partition and grow the root partition.

If anyone has the command string to use to get it to fix the errors, I'd appreciate it.

The e2fsck command I ran last night seemed to work for a while and then it hung up. It also doesn't seem to print any progress reports. Does anyone have a command that will print out the progress as its going as well?

Statik

---

### Post by wilee-nilee on 2009-09-12
Have any of these partition spaces been part of a dual boot with a additional OS ? What I have found with repartitioning is that moving a partition to figuratively right or left is only possible if you are doing it with a original install in the partition even if you delete a portion and reformat it, I hope this makes sense. You might consider saving all the back ups you need and just repartition the whole hard drive. I think you will get more qualified help if you post the operating system or systems that you are using and have used.  good luck

---

### Post by Bartender on 2009-09-12
> **Statik said:**
> I am using gparted

I am booting from the live CD so that the HD partitions are unmounted.

A real GParted LiveCD or an Ubuntu LiveCD?  I suspect you mean Ubuntu LiveCD.  Not gonna work.  

Follow the link under my sig.  Download the latest stable version of Gparted LiveCD.  Burn it as an .iso.  You will end up with a partitioner that will boot the PC and it doesn't mount any partitions.

Here's what I'd do - not an expert or anything, so anyone else please jump right in - 
#1: Is the 5 Gib area unpartitioned or unallocated?  If it's partitioned delete it so that it's unallocated.  Apply the changes.  It's critical to apply your changes at each step.  Otherwise GParted will let the tasks stack up and try to do them all at once.
#2: Move the /home partition.  Move it so that it is right up against the swap.  Apply.  There is also a "Copy" command within GParted.  If you go to the GParted website you'll find some tutorials with pictures and stuff.  [Here's]("http://gparted.sourceforge.net/larry/resize/resizing.htm") one of them just to get you started.
#3:  You should now have unallocated space between / and /home.  Expand / into the unallocated space.  Apply.

Get out of GParted LIveCD, restart, and cross your fingers.

---

### Post by P4man on 2009-09-12
His problem is those read errors, not the partitioning (thats just exposing the real problem). Im no expert in e2fsck either though, and I guess your googling skills arent any worse then mine, so google :)
I would be warry the disk might be dying though, before doing anything else, Id make a backup.

---

### Post by Statik on 2009-09-13
Well, I found the command I need, I think:
```
sudo e2fsck -f -c -C0 -k /dev/sda6
```

I first just ran:
```
sudo fsck /dev/sda6
```

and that found some stuff. Now the above one is checking every block and has a progress indicator too!

Statik

---

