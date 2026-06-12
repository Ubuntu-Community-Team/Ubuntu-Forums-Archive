---
title: "Incomplete GParted resizing could've screwed up my HDD?"
date: 2012-01-10
forum: General Help
---

### Post by Crisopa on 2012-01-10
Today i found an old Pentium 4 IBM computer occupying room room, so i told myself "why not" and decided to run a Lubuntu Live CD. However, it wasn't able to boot USB drives, so i had to burn a cd. Ok, everything fine, although terribly slow (probably because of the single RAM of 256MB)... And because the data contained in the HDD was so old, i decided to use GParted; after all, those files were irrelevant to me.
 
Thing is, it ran at a speed slower than that of the rotation of the planet Mercury and inevitably crashed (popped up a message saying that the operation couldn't complete). After i clicked "Ok", the partitions list "grayed out" and now they won't show anymore.
 
**In short**: did GParted (plus a combination of horrible hardware, maybe time and high failure rates) screw my HDD? And if the answer is yes, does it have any solution? It was a an old 40GB Western Digital.

---

### Post by Double.J on 2012-01-10
> **Crisopa said:**
> Today i found an old Pentium 4 IBM computer occupying room room, so i told myself "why not" and decided to run a Lubuntu Live CD. However, it wasn't able to boot USB drives, so i had to burn a cd. Ok, everything fine, although terribly slow (probably because of the single RAM of 256MB)... And because the data contained in the HDD was so old, i decided to use GParted; after all, those files were irrelevant to me.
 
Thing is, it ran at a speed slower than that of the rotation of the planet Mercury and inevitably crashed (popped up a message saying that the operation couldn't complete). After i clicked "Ok", the partitions list "grayed out" and now they won't show anymore.
 
**In short**: did GParted (plus a combination of horrible hardware, maybe time and high failure rates) screw my HDD? And if the answer is yes, does it have any solution? It was a an old 40GB Western Digital.

Hi there!

Did you have data to be saved?

If yes, do absolutely nothing, make sure the drive stays unmounted, download [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") and scan the disc to see what you can get

If no - you were just setting up the drive and it doesn't matter if anything on there is gone, then click on device, create partition table and use the default mbr setting - it should now go white and become editable again.

Did you build up a long list of things for gparted to do before clicking apply? I've had errors before doing this -learned the hard way it's best to click apply after each modification you want to write. 

Also with very little ram, give it a hand by creating a 1gb swap partition, right clicking and choosing 'swapon' - Ram wasn't the problem, but it's a precaustion I've taken before when using hardware with very low ram - reduces the risk of a halt mid data copying!

---

### Post by marinara on 2012-01-11
almost certainly you have a bad hard disk.  burn it with fire before it tricks you into putting quality time or quality data on it.

I can't be sure, because you didn't say what you did exactly with gparted.  besides, the lubuntu cd lets you repartition the disk in a single step.  Did you know that?

---

### Post by Double.J on 2012-01-11
> **marinara said:**
> almost certainly you have a bad hard disk.  burn it with fire before it tricks you into putting quality time or quality data on it.

I can't be sure, because you didn't say what you did exactly with gparted.  besides, the lubuntu cd lets you repartition the disk in a single step.  Did you know that?

Whilst the age of the drive increases the risk of hard drive failure, gparted failing to write changes to a disk is not usually indicative of this. 

Also the OP may well have reason to configure the hardrive manually for example separate /home, /boot or more partitions, dual booting, just seeing how the drive is currently partitioned without running an installer, or at a push for a machine of this age to use a different partition table.

---

### Post by Crisopa on 2012-01-11
> **gnu/mirow said:**
> Hi there!

Did you have data to be saved?
 
Not exactly, that data ain't mine, the HDD came with the computer, so  given the time it's been stored and the fact that the original owner  didn't claim any data before, that made me want to experiment with this  machine. There's however, a dim curiosity to know if it used to store  anything "dirty" (although it was owned by a relative, so whatever it  is/was i probably know already).

> **gnu/mirow said:**
> If yes, do absolutely nothing, make sure the drive stays unmounted, download [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") and scan the disc to see what you can get

I downloaded it, but couldn't sort it out, so i'm willing to wipe it out.

> **gnu/mirow said:**
> If no - you were just setting up the drive and  it doesn't matter if anything on there is gone, then click on device,  create partition table and use the default mbr setting - it should now  go white and become editable again.

That's it! That's what i wanna do now, but how? I click on device on where, File Manager, Disk Utility or GParted?

> **gnu/mirow said:**
> Did you build up a long list of things for  gparted to do before clicking apply? I've had errors before doing this  -learned the hard way it's best to click apply after each modification  you want to write.

No, i only wanted to shrink the main partition to make room for Lubuntu;  but i guess that wasn't very wise from me considering how slow the thing was  to begin with (i upgraded it to 500MB, which is fine now).

> **gnu/mirow said:**
> Also with very little ram, give it a hand by  creating a 1gb swap partition, right clicking and choosing 'swapon' -  Ram wasn't the problem, but it's a precaustion I've taken before when  using hardware with very low ram - reduces the risk of a halt mid data  copying!

Now that it has half one gig it's like "fine", but i'll make sure to give it a reasonable ammount of swap.

> **marinara said:**
> almost certainly you have a bad hard disk.  burn it with fire before it tricks you into putting quality time or quality data on it.

I can't be sure, because you didn't say what you did exactly with gparted.  besides, the lubuntu cd lets you repartition the disk in a single step.  Did you know that?

I was about to try the magnets, but decided to give it a chance. If after all the hassle, it's still too stubborn to respond, i'll disassemble it and craft me some neat thingies with the plates.

---

### Post by hhh on 2012-01-11
> **Crisopa said:**
> That's it! That's what i wanna do now, but how? I click on device on where, File Manager, Disk Utility or GParted?
With no partitons mounted (like from a Live CD), open GParted, go to the "Device" menu at the top, choose "Create partition table...", apply the action. After that you can right-click the blank partition and format a new partition as ext4.

---

### Post by xyzzyman on 2012-01-11
[http://support.wdc.com/product/download.asp?groupid=502&sid=30&lang=en](http://support.wdc.com/product/download.asp?groupid=502&sid=30&lang=en)

Burn that ISO and then you can run an extended test and the HDD just to make sure if the drive is still viable or not. 

With that said, being a P4 you might be lucky and it'll support DDR2 and you could pick up RAM cheap. I haven't looked at DDR pricing in awhile plus you may be even more limited in what it'll accept if it's DDR. Otherwise you're looking at running lubuntu to not have the system run at a crawl with alot of swapping.

---

### Post by leclerc65 on 2012-01-11
> No, i only wanted to shrink the main partition 
Delete then New (partition) is much faster than Shrink, even on fast computer. If you need the data , save it first.

---

