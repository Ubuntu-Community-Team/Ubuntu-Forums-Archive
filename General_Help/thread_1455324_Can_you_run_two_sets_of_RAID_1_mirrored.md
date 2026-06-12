---
title: "Can you run two sets of RAID 1 mirrored?"
date: 2010-04-15
forum: General Help
---

### Post by Roasted on 2010-04-15
I have 4 drives. Two identical pairs. Each pair does something different and serves a different purpose to my system. Can I set up two RAID 1 arrays?

500gb/500gb = Raid 1
250gb/250gb = Raid 1

Can I do this with Ubuntu's software raid?

---

### Post by falconindy on 2010-04-15
Sure, you'll end up with a /dev/md0 and /dev/md1.

---

### Post by Roasted on 2010-04-16
If I dual boot the first 500gb drive with Vista/Ubuntu, could I still run Ubuntu in Raid 1 mirror with the other 500gb drive? Or do they have to be identical in partition structure too? If so, I can slap in an 80gb SATA drive to run as stand-alone for Vista and dual boot it with the pair of RAID 1 mirrors... making it:

Vista - 80gb drive - non raid
500gb/500gb - raid 1
250gb/250gb - raid 1

Also - how would I get software raid set up? I've never set it up before...

---

### Post by marshmallow1304 on 2010-04-16
From what I've read, you can set up software RAID on any identical partitions, regardless of hard drive structure.  Then again, I've never done it and nearly all I know about RAID comes from [this page]("https://help.ubuntu.com/community/Installation/SoftwareRAID").

---

### Post by falconindy on 2010-04-16
> **Roasted said:**
> If I dual boot the first 500gb drive with Vista/Ubuntu, could I still run Ubuntu in Raid 1 mirror with the other 500gb drive? Or do they have to be identical in partition structure too? If so, I can slap in an 80gb SATA drive to run as stand-alone for Vista and dual boot it with the pair of RAID 1 mirrors... making it:

Vista - 80gb drive - non raid
500gb/500gb - raid 1
250gb/250gb - raid 1

Also - how would I get software raid set up? I've never set it up before...
If you use software RAID, you won't be able to access those drives (safely) from Windows.

Google returns [this](http://ubuntuforums.org/showthread.php?t=408461) when searching for 'ubuntu mdadm'. It's a fairly simple process, you just need to be precise.

---

### Post by Roasted on 2010-04-16
> **falconindy said:**
> If you use software RAID, you won't be able to access those drives (safely) from Windows.



This comment confused me. How would I be able to access them anyway since those Linux partitions are EXT4? Or are you saying, basically don't bother trying to do 100gb Vista/400gb Ubuntu and software raiding Ubuntu's 400gb partition to a 500gb partition?

---

### Post by falconindy on 2010-04-16
> **Roasted said:**
> This comment confused me. How would I be able to access them anyway since those Linux partitions are EXT4? 
Yeah fair enough. I thought you might be interested in using Ext3 and that sketch ext3fs driver for Windows. "Sandboxing" Vista in a 80gb partition and leaving the rest for RAID sounds fine to me.

[QUOTE=Roasted]Or are you saying, basically don't bother trying to do 100gb Vista/400gb Ubuntu and software raiding Ubuntu's 400gb partition to a 500gb partition?[/quote]
That wasn't my implication, but I wouldn't do this either. Since the size of a RAID1 array is the size of the smallest drive in the array multiplied by the number of members (2 in this case), you'd be missing out on 100gb.

---

### Post by FiReiSFuN on 2010-04-16
Here is what you could do. Let's take the two 500GB drives first (say for argument they are /dev/sda and /dev/sdb). 

Partition 1 - Vista (100GB NTFS)
Partition 2 - Ubuntu Boot (500MB ext2)
Partition 3 - Ubuntu (399GB ext3)
Partition 4 - 500MB Swap

Then, make the identical parition layout on drive /dev/sdb. You would then software raid the Ubuntu boot partitions into /dev/md0, the Ubuntu partitions into /dev/md1, and the swaps into /dev/md2. You would then have your Vista partition on your main drive, and another 100GBs to format as NTFS for windows storage.

Of course, with this setup, if your drive /dev/sda took a dump, then you would still be able to boot into ubuntu via /dev/sdb, but you would lose all of your Vista stuff. But you are asking about Linux RAID! So I'm not too worried about Windows solutions.

Caveat: If your drives already have data on them, its slightly more difficult to do this setup because you essentially have to make your RAID 1 devices with only /dev/sdb, then copy all data from /dev/sda to your new /dev/md* partitions, then add /dev/sda's partitions and watch /proc/mdstat as they are sync'ed up!

---

### Post by falconindy on 2010-04-16
> **FiReiSFuN said:**
> Partition 1 - Vista (100GB NTFS)
**Partition 2 - Ubuntu Boot (500MB ext2)**
Partition 3 - Ubuntu (399GB ext3)
Partition 4 - 500MB Swap

I know Ubuntu enjoys keeping around every last kernel it ever found, but 500mb is enormous for a boot partition. 50mb is a little too small, but 100mb is more than sufficient. Regardless, a /boot partition isn't necessary with RAID-1, even if you're using grub-legacy. Since the drives are a mirror, there's no issues reading a drive individually. You will, however, want to install GRUB to the MBR of both drives.

Given that the OP mentioned an 80gb drive dedicated to Vista, I would lay out the larger pair of drives as such...

```
____1_________________2___________
|       |                         |
| 250mb |    remainder of drive   |
|_______|_________________________|

```
the 250mb is assigned to swap, and the remainder of the drive is dedicated to the raid array. With multiple swap partitions, they're automatically striped to increase performance.

The smaller pair of drives should be entirely dedicated to raid and be used for the root filesystem.

---

### Post by Roasted on 2010-04-16
I've never even installed boot on a separate partition. I've always done:

1gb Swap
15gb Root
Remainder as Home

---

### Post by falconindy on 2010-04-16
That's fine, except you can't partition a raid device like you can a regular block device. I would suggest using LVM on top of the RAID-1 partition. This allows you to resize partitions on the fly should you ever need to adjust them, rather than relying on hard set numbers that may or may not fit your needs 6 months from now.

---

### Post by ratcheer on 2010-04-16
I would configure the four drives as RAID 1+0 (aka RAID 10). This means mirror one pair of drives, mirror the other pair of drives, then create a RAID 0 "stripe set" of the two sets of mirrors. This will give you not only total redundancy, but improved performance.

I am assuming your hardware and software will support this, but I don't know about that.

Tim

---

### Post by Roasted on 2010-04-16
> **falconindy said:**
> That's fine, except you can't partition a raid device like you can a regular block device. I would suggest using LVM on top of the RAID-1 partition. This allows you to resize partitions on the fly should you ever need to adjust them, rather than relying on hard set numbers that may or may not fit your needs 6 months from now.

I've used this same partitioning method since 2005, and I've never had a need to do anything other than this. Since my current partition structure is likely to suffice for in the future, I suppose LVM isn't necessary?

I doubt my hardware supports it... I really just want to have two sets of mirroring, and I'm golden. I have another backup server that's just raw data images and whatnot, so any more redundancy isn't needed, not to mention I doubt I can support it.

---

### Post by falconindy on 2010-04-16
The LVM suggestion was nothing but a suggestion. Figured I'd let you know it's out there.

I'm not sure why you have any doubts as to your **hardware** supporting it when its strictly a **software** based implementation.

---

### Post by Roasted on 2010-04-17
Say I set up software raid through Ubuntu, and one drive fails - do I get a warning message notifying me?

I think since I have a spare rig I might put 2 spare same-size drives I have in there to get used to how to get it running prior to trying it on my main system...

---

### Post by falconindy on 2010-04-17
There's definitely monitoring tools available that can alert you if a drive is failing. The tools I'm familiar with are command line based and just send mail. I'm not aware of GUI based utils, but they probably exist.

---

### Post by Roasted on 2010-05-08
Okay - I'm ready to upgrade to 10.04 with a fresh install. What should I do to get started? Should I branch Windows off on another drive? Or should I try to run software raid with Windows also residing on the drive? 

I'm just kind of drawing a blank on what exactly I do. Should raid be set up during the install process? Or do I install Ubuntu and THEN configure it?

---

### Post by Roasted on 2010-05-09
So I found this video:

[http://www.youtube.com/watch?v=S3nWXn934H0](http://www.youtube.com/watch?v=S3nWXn934H0)

Questions:

1 - With what he's doing, can I do that across two drives with different partitioning structure? Or do the drives have to be 100% identical?

2 - If I do this with 10.04 and get it running, then 10.10 comes out and I do a fresh install, will I have to redo this whole setup? Or will the RAID settings somehow be stored in my home directory (which doesn't get formatted) therefore retaining the array?

---

