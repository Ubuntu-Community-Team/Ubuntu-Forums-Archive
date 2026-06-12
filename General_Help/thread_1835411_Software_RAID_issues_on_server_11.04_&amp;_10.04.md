---
title: "Software RAID issues on server 11.04 &amp; 10.04"
date: 2011-08-29
forum: General Help
---

### Post by the_dingman on 2011-08-29
Hey everyone,

I'm trying to set up a home file server using (5)qty 1.5TB Seagate Green drives in a RAID 5 configuration.  I have an Asus E35M1-I board with an AMD E-350 CPU.  I'm having issues with the server locking and resetting any time I try to transfer files to it, but only when using the RAID set-up (in troubleshooting, I installed to one drive and it was solid).

I've tried server versions 10.04 32bit, 11.04 64bit and 11.04 32bit, and all give the same issue.

Around 50% of the time my crash follows the following error:

NOHZ: local_softirq_pending 08

Google searches are giving me results that are over my level of Linux understanding.  Any help or ideas would be appreciated.

My basic setup is 2GB of SWAP per drive (tried both with and without creating a software RAID array for SWAP), and the rest of each drive allocated for RAID, mounted as "/".

---

### Post by Ed_Ziffel on 2011-08-29
YOu have to set up the hard drives as a volume for a raid  before you partition them.  You do this when at the partitioner in the install.  set up each drive as a volumne for a raid drive when in the section where you select the type partition. the use the raid tools in the partitioner menu to create the raid form the drives.  Did not really read your post to closely but if you set up the raid right, then I don't think it is possible to assign individual drives as having part of the swap file.  Not real sure but tried to do something like it with no luck.  

Also the ubuntu servers use MBR for disk management.  That means that the biggest partition you can use on your raid is 2tb. There is a way to use GPT/GUID so that you can have partitions bigger than you can build at this time, but doing that requires you to recompile the install disks which is over my head.

---

### Post by the_dingman on 2011-08-29
I had the partitions set up for raid and got through the install.  I've been able to copy small transfers to the server, but it crashes when I throw a few GB at it in one shot.

I have gotten far enough to get ubuntu-desktop installed to play with the system diagnostic tools a bit.  The problem isn't about getting the partitions or RAID set up, it's with crashing on transferring files.

I'm currently working on trying a separate 80GB drive with the system and SWAP, and the RAID array just for storage.  Hopefully it solves the problem.

---

### Post by Seq on 2011-08-29
> **Ed_Ziffel said:**
> YOu have to set up the hard drives as a volume for a raid  before you partition them.  You do this when at the partitioner in the install.  set up each drive as a volumne for a raid drive when in the section where you select the type partition. the use the raid tools in the partitioner menu to create the raid form the drives.  Did not really read your post to closely but if you set up the raid right, then I don't think it is possible to assign individual drives as having part of the swap file.  Not real sure but tried to do something like it with no luck.

`md` arrays can be done on any block device. My setup uses md raid devices on partitions without issue.

/dev/md0 is composed of /dev/sd[a,b,c,d]1, is 500MB raid1. (I copied the boot sector across all four drives so I could lose the first drive and reboot without issue)

/dev/md1 is composed of /dev/sd[a,b,c,d]2, is currently the remainder of the 500GB drives. It is raid 5.

> **Ed_Ziffel said:**
> Also the ubuntu servers use MBR for disk management.  That means that the biggest partition you can use on your raid is 2tb. There is a way to use GPT/GUID so that you can have partitions bigger than you can build at this time, but doing that requires you to recompile the install disks which is over my head.

There is no need for partitions on the raid array, so /dev/md1 is an LVM pvs as-is, which contains a bunch of filesystems on top. Likewise, /dev/md0 is a plain ext4 partition, again without a partition table on it.

Regarding GPT disks on BIOS machines, I just actually did this for the first time recently. If you're booting a system straight from LVM (possibly other scenarios), you will need to have an additional 1MB grub partition at the (preferably) start of your drive to give grub somewhere to embed itself, since gpt doesn't quite leave enough room for everything.

---

### Post by Seq on 2011-08-29
> **the_dingman said:**
> I'm trying to set up a home file server using (5)qty 1.5TB Seagate Green drives in a RAID 5 configuration.  I have an Asus E35M1-I board with an AMD E-350 CPU.  I'm having issues with the server locking and resetting any time I try to transfer files to it, but only when using the RAID set-up (in troubleshooting, I installed to one drive and it was solid).

Have you ruled out power as an issue? What kind of power supply do you have on this?

You managed to install to the RAID, but it crashes whenever you try to write to it? Just booting the system causes some writes to happen (log files, etc).

Also, I kind of assumed you were making software raid with mdadm. Is this the case, or are you using some motherboard-based softraid functionality? Or maybe a real raid card?If that is the case, my last post regarding partitioning and raid setup might not apply.

> **the_dingman said:**
> My basic setup is 2GB of SWAP per drive (tried both with and without creating a software RAID array for SWAP), and the rest of each drive allocated for RAID, mounted as "/".

You would probably be better with swap on the raid array than off it. Simply for speed: Having 8GB swap across a raid5 array is going to be better than 5x2GB in terms of speed if you ever need to use swap, and uses the same amount of disk space. (If you ever need 8GB of swap on a home server, buy more memory).

If I were you, I'd look into LVM if you haven't already. A bit of a learning curve, but it will allow you to slice up the RAID array very nicely, allowing you to resize things as needed. ("/" needs to be 5GB bigger? Two commands, and you don't even need to reboot).

---

### Post by the_dingman on 2011-08-29
My problem HAS to do with how the network interacts with the RAID array...  Here is my most recent install:

Ubuntu 11.04 64bit installed on an 80GB SATA Drive
5x 1.5TB drives on SATA ports 2-6

Software RAID set up in Ubuntu's disk manager

When I transfer ~20GB to the 80GB drive over the network, then copy the files to the RAID array inside Ubuntu desktop, everything is fine.  When I share the RAID array directly, then copy to that, my system hardlocks.

---

