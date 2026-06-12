---
title: "FSTAB &amp; Mdadm Confusion"
date: 2011-02-25
forum: General Help
---

### Post by cpressland on 2011-02-25
Hey there,

So I've just setup a new storage server, pretty basic layout as follows:

/dev/sda1 [250GB HDD] /
/dev/sda2 [250GB HDD] SWAP

/dev/sdb1 [2000GB] RAID
/dev/sdc1 [2000GB] RAID
/dev/sdd1 [2000GB] RAID
/dev/sde1 [2000GB] RAID

The four raid devices are in a RAID5 MDADM Software RAID @ /dev/md_d0

It's been Syncing for a few days and got to 14% so far, so I've decided to start loading content onto it, but one thing I've noticed is that I'm manually mounting /dev/md_d0 @ /home/storage. I want this to be handled by fstab.

Can somebody provide me with the correct Syntax to mount a EXT4 Filesystem in a Software RAID at boot time.

This idealy needs to happen early in the boot as I have various things being pulled from this partition, example settings.json for transmission.

Any ideas?

Thanks Guys

Chris

---

### Post by Ocxic on 2011-02-25
add this line to your /etc/fstab

```

/dev/md_d0    /home/storage    ext4    defaults    0    2

```
```

^--Device       ^--Mount point   ^-FS type  ^-permissions   (the numbers 0 and 2 are for error checking i believe)

```

---

### Post by YesWeCan on 2011-02-25
Several days and only 14% sync'd! :o Is that normal?

Just a reminder to make sure you have set up your ARRAY directive in your mdadm.conf.

---

### Post by cpressland on 2011-02-25
Thanks for the code,

@YesWeCan - Sorry to sound like a complete idiot here, this is my first time with a software array and I've had virtually no help with it. Whats the ARRAY directive?

---

### Post by YesWeCan on 2011-02-25
No need to apologize! We're all novices at some aspect of linux. I'm not exactly a raid expert by any means.
Would you mind posting the output of
cat /etc/mdadm/mdadm.conf

and put it in code tags (highlight and click #)

and also the output of
sudo mdadm --examine --scan

---

### Post by cpressland on 2011-02-25
> **YesWeCan said:**
> No need to apologize! We're all novices at aspect of linux. I'm not exactly a raid expert by any means.
Would you mind posting the output of
cat /etc/mdadm/mdadm.conf

and put it in code tags (highlight and click #)

and also the output of
sudo mdadm --examine --scan

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Thu, 24 Feb 2011 18:05:38 +0000
# by mkconf $Id$
```

&

```
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726
   spares=1
```

---

### Post by YesWeCan on 2011-02-25
Looks good.
You just need to add that ARRAY line to the end of the mdadm.conf file.
Back up the file for good measure
cd /etc/mdadm
sudo cp mdadm.conf mdadm.conf.bak

Edit the file manually or use 

sudo sh -c "mdadm --examine --scan >> /etc/mdadm/mdadm.conf"


This tells mdadm how to assemble the array at boot up.

---

### Post by YesWeCan on 2011-02-25
Actually, there is a slight problem here. You said your array is at /dev/md_d0 but the scan says the array is meant to be at /dev/md0.

So I think you need to make the fstab entry use /dev/md0

Then when you reboot it should mount the array correctly at /dev/md0.

---

### Post by cpressland on 2011-02-25
Thanks man, I really appreciate this. I've just got to finish copying another 900 or so Gig to this array then I'll make those changes and reboot.

Once confirmed, I'll mark the thread as Solved.

Thankyou so much.

So am I adding the line as:

```
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726
   spares=1
```

```
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726 spares=1
```

or

```
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726
```

---

### Post by YesWeCan on 2011-02-25
Probably the second or the third (everything on the same line).
It depends whether you are intending to have a spare disk, ie: you are setting up a 3 disk RAID 5 with a spare disk that is left over and not used unless a disk fails.

What command did you use to create the array in the first place?

Please post the output of:
sudo mdadm --detail /dev/md0

and

cat /proc/mdstat

---

### Post by rubylaser on 2011-02-25
No, a few days to sync (4) 2TB drives is very slow.  Can, you paste the output of
```
cat /proc/mdstat
```

Also, have you tried to change the sync speed variables for the raid array?
```
echo 50000 > /proc/sys/dev/raid/speed_limit_min
echo 200000 > /proc/sys/dev/raid/speed_limit_max
```

That should make it go faster.

---

### Post by cpressland on 2011-02-25
```
/dev/md_d0:
        Version : 00.90
  Creation Time : Thu Feb 24 18:09:27 2011
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Feb 26 01:21:51 2011
          State : active, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 15% complete

           UUID : 8906318d:50dc25cc:ef9b5c7a:c6693726 (local to host Galactica)
         Events : 0.4551

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       4       8       65        3      spare rebuilding   /dev/sde1
```


&

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : active raid5 sdb1[0] sdd1[2] sde1[4] sdc1[1]
      5860535808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]
      [===>.................]  recovery = 15.1% (296580276/1953511936) finish=18702.4min speed=1476K/sec
      
unused devices: <none>

```

---

### Post by YesWeCan on 2011-02-25
OK, so you want to use the last of those ARRAY lines, without the spare=1

Then reboot it and check it has mounted. mdstat should show it as md0

That 18k minutes/300 hours resync time is bogus. See what it says after a reboot.

---

### Post by rubylaser on 2011-02-25
1476K/sec is ridiculously slow.  If you do reboot, please make sure to open a terminal window, and then do what I mentioned before...
```
sudo -i
echo 50000 > /proc/sys/dev/raid/speed_limit_min
echo 200000 > /proc/sys/dev/raid/speed_limit_max
```

You should see speed an order of magnitude faster than that.

---

### Post by rubylaser on 2011-02-25
> That 18k minutes/30 hours resync time is bogus. See what it says after a reboot.
18,702 minutes = 12.9875 days :) That's the highest re-sync time I've ever seen without having a massive array involved.

---

### Post by YesWeCan on 2011-02-25
Well it would suggest ZX80 hardware. :P

---

### Post by cpressland on 2011-02-26
> **rubylaser said:**
> 1476K/sec is ridiculously slow.  If you do reboot, please make sure to open a terminal window, and then do what I mentioned before...
```
sudo -i
echo 50000 > /proc/sys/dev/raid/speed_limit_min
echo 200000 > /proc/sys/dev/raid/speed_limit_max
```

You should see speed an order of magnitude faster than that.

Okay guys, the last 100GB is copying now. Once done I'll reboot with the updated Mdadm file, edit fstab and run the echo commands.

I have already run those commands and it's made no difference, so I'm guessing a reboot is in order. Shouldn't take much longer to finish copying.

So by my understanding boot should be going like this:

Linux Base System
MDADM RAID Initialisation
FileSystem Mounts
Rest of Linux Services.

I've just got an issue if Transmission-Daemon starts before /dev/md0 is mounted due to it's settings.json file being Symlinked from there. We'll see on the next reboot.

---

### Post by cpressland on 2011-02-26
Okay, I rebooted and everything came back online properly, and now the drive is mounted at /dev/md0 /home/storage

BUT, the syncing has started from scratch and it's saying it'll be 8374 minutes till finish. I've used the 

echo 50000 > /proc/sys/dev/raid/speed_limit_min
echo 200000 > /proc/sys/dev/raid/speed_limit_max

Commands, but it's running the sync at 4228K/sec. How can I get this to speed up?

```
/dev/md0:
        Version : 00.90
  Creation Time : Thu Feb 24 18:09:27 2011
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Feb 26 11:54:44 2011
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 8906318d:50dc25cc:ef9b5c7a:c6693726 (local to host Galactica)
         Events : 0.7244

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       4       8       65        3      spare rebuilding   /dev/sde1

```

Now  by my understanding of this layout, if /dev/sdc was to fail, /dev/sde would take over it's job, then I could replace /dev/sdc with a new drive and resync everything? Sounds good to me.

Right now I just want the sync to speed up.

---

### Post by rubylaser on 2011-02-26
Are these drives connected to the SATA heads on the motherboard or to a controller card?  I ask, because even without tuning anything, your array should be faster than this.  It's almost acting like it's maxing out it's connection, which shouldn't be possible at the speed they're currently going even if they're all connected to a PCI SATA card.

> Well it would suggest ZX80 hardware. 
Can you list your hardware here to please?

---

### Post by cpressland on 2011-02-26
Sure, it's a brand new [HP Proliant MicroServer]("http://h18004.www1.hp.com/products/quickspecs/13716_na/13716_na.pdf").

All drives are connected via SATA directly to the motherboard, no controller pci card is in use, albeit after this it's something I'm going to look into.

Thing that confuses me is the RAID is able to move TBs of Data overnight no problem, yet this sync is just taking an age.

---

### Post by rubylaser on 2011-02-26
That's not exactly a powerhouse, so you're relying on the processor to do all the parity calculations in mdadm.  Have you even looked at the load via the top command while the array is syncing?  I Bet you're being slowed by the processor, not the disks.  And, how much RAM do you have?

Also, there are a couple of extra tunables that you can try to see if it helps speed it up...

```

blockdev --setra 16384 /dev/sd[bcde]

echo 1024 > /sys/block/sdb/queue/read_ahead_kb
echo 1024 > /sys/block/sdc/queue/read_ahead_kb
echo 1024 > /sys/block/sdd/queue/read_ahead_kb
echo 1024 > /sys/block/sde/queue/read_ahead_kb

echo 256 > /sys/block/sdb/queue/nr_requests
echo 256 > /sys/block/sdc/queue/nr_requests
echo 256 > /sys/block/sdd/queue/nr_requests
echo 256 > /sys/block/sde/queue/nr_requests

# Set read-ahead.
echo "Setting read-ahead to 64 MiB for /dev/md0"
blockdev --setra 65536 /dev/md0

# Set stripe-cache_size for RAID5.
echo "Setting stripe_cache_size to 16 MiB for /dev/md0"
echo 16384 > /sys/block/md0/md/stripe_cache_size

```

---

### Post by cpressland on 2011-02-26
I've been keeping an eye on TOP. md0_RAID5 is using 8% CPU and md0_resync is using 0%. So I don't think the CPU is bottlenecking things at this point, if it was maxed out, fair enough, but it's baring hitting the 10% area.

At the moment the system is running 1GB of RAM, planning to up it to 4GB soon once this thing goes into production.

---

### Post by cpressland on 2011-02-26
Just ran those scripts, now it's running at

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[1] sdd1[2] sdb1[0] sde1[4]
      5860535808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  0.5% (11509588/1953511936) finish=980.8min speed=32996K/sec
      
unused devices: <none>
```

MUCH Faster. 16 Hours over 16 days anytime!

---

### Post by rubylaser on 2011-02-26
Good, that's much better.  That's now in the normal speed range.  On the low end of the range, but normal :)  My RAID6 array is a similar size to yours, but with ( 8 ) 1TB disks.  Mine is able to sync in about 560 minutes, so there's still room for improvement. But if your data transfer speeds once it's synced aren't slow, I wouldn't worry about any further tweaking.

If you look at top now, mdadm should be using more RAM and processor at this point.

---

### Post by YesWeCan on 2011-02-26
> **cpressland said:**
> Okay, I rebooted and everything came back online properly, and now the drive is mounted at /dev/md0 /home/storage
Good.
> BUT, the syncing has started from scratch and it's saying it'll be 8374 minutes till finish.
Well, it has resumed with only(!) 140 hours to go. That's a lot shorter. Probably because you aren't copying data to it now.

> Now  by my understanding of this layout, if /dev/sdc was to fail, /dev/sde would take over it's job, then I could replace /dev/sdc with a new drive and resync everything? Sounds good to me.
I think you have a 4 disk RAID and one disk is re-syncing. So you don't have any spares. mdadm says you have a spare but it is lying. Why it says this I don't know - silly. I had the same confusion when I pulled the power cord on my RAID10 while it was being written to, as a test, and when it rebooted one of my disks was described as a spare and started resyncing. Misleading, unecessary.

---

### Post by rubylaser on 2011-02-26
Luckily, with a few tweaks, it's going a lot faster now, only ~16 hours to sync.

In regards to the spare showing up, when an array is rebuilding, this is a much more valuable line to look at.

> State : clean, degraded, recovering

Or, just view the status of cat /proc/mdstat

---

### Post by YesWeCan on 2011-02-26
> **rubylaser said:**
> Luckily, with a few tweaks, it's going a lot faster now, only ~16 hours to sync.
Yes your tweaks have had an awesome effect.

I suppose I should be careful not encourage anyone to pull the plug on a RAID 5 or RAID 6 while it is writing. I understand this has potential to create a parity block error that is not detected on power-up and can, over time, propagate and render the array unrecoverable when a disk fails. :(

---

### Post by cpressland on 2011-02-26
So tell me guys, what would happen if a drive randomly failed? After Syncing of course.

---

### Post by rubylaser on 2011-02-26
> I suppose I should be careful not encourage anyone to pull the plug on a RAID 5 or RAID 6 while it is writing. I understand this has potential to create a parity block error that is not detected on power-up and can, over time, propagate and render the array unrecoverable when a disk fails.

It kind of like poking a bear to see what happens.  I don't see people trying to intentionally break their hardware arrays, but often people try to do it with software arrays, because they want to understand how it works.  The best thing to do is have redundancy, your server hooked up to  a UPS, with power management turned on so the server will safely shutdown in the event of a loss of power, run SMART on your disks, let mdadm run it's periodic consistency checks, and most importantly, good backups.

---

### Post by rubylaser on 2011-02-26
> So tell me guys, what would happen if a drive randomly failed? After Syncing of course.


Well, you'd fix it of course :)  Seriously, you'd shut off the box, pull out the defective hard drive, pop a replacement in, and add the new disk back in like this...
```
mdadm --manage /dev/md0 --add /dev/sdb1
```

You'd see the array re-sync, and you'd be back in business.  While it's re-syncing, you'd still have access to your data even in it's degraded state, access would be slower as it's rebuilding though.

---

### Post by cpressland on 2011-02-26
Badass, would I need to remove said /dev/sdb1 from the array first or simply readd the new drive after partitioning?

---

### Post by YesWeCan on 2011-02-26
Here's the thing. With a RAID 5, once one disk is lost anything that causes another disk to be unreadable will cost you the whole array. So you probably don't want to do anything other than either backing it up or rebuilding it. No writing. If something goes wrong while you are writing, like a power-cut or a loose cable or anything else, your whole array is toast. A degraded RAID 5 is more dangerous than no RAID at all.

---

### Post by cpressland on 2011-02-26
So as long as I replace the failed drive ASAP I'm all good? So on a healthy array it can handle a power failure so long as I run the usual FileSystem diagnostics, but on a degraded array it can cause serious problems?

---

### Post by cpressland on 2011-02-26
Well, I just rebooted it and it's not come back online. No idea why as I've been working on it over SSH. Any ideas? Going to plug in a monitor shortly.

---

### Post by cpressland on 2011-02-26
K, it's giving me the error /dev/md0 does not appear to be active. Completely clueless at this point how it could be working fine, and now it's completely fubar.

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sde1[4](S) sdc1[1](S) sdb1[0](S) sdd1[2](S)
      7814047744 blocks
       
unused devices: <none>
```

What it looks like has happened is the server rebooted and /dev/sda decided to become /dev/sde killing the array, now that I've rebooted it's gone back to /dev/sda but now the drives won't do a darn thing.

Any ideas?

---

### Post by cpressland on 2011-02-26
Managed to get the array online again via: mdadm --manage /dev/md0 -R

But on reboot it'll begin resyncing again from scratch because all the drives get different /dev/sd* points.

Solution?

---

### Post by rubylaser on 2011-02-26
I'm sorry if I missed it, but what do you have in your /etc/mdadm/mdadm.conf file.  Disk order doesn't matter to mdadm as each disk stores the UUID on the superblock.  It knows the disk belongs to that array based on that info.  It should look something like this.
```
DEVICE partitions
HOMEHOST fileserver
MAILADDR root@localhost
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41
```
Also, I can't remember if you mentioned earlier; Are these Green drives?

---

### Post by rubylaser on 2011-02-26
> Badass, would I need to remove said /dev/sdb1 from the array first or simply readd the new drive after partitioning?

Once, it's out of the machine, it's effectively removed, so you'd just re-add the new partitioned drive, and it'd add it to the array.  It's very slick :)

---

### Post by gsgleason on 2011-02-26
> **rubylaser said:**
> Once, it's out of the machine, it's effectively removed, so you'd just re-add the new partitioned drive, and it'd add it to the array.  It's very slick :)

The spare that you had is for this purpose.  It's is standby, and when one drive fails, it will automatically activate the spare and sync.

---

### Post by rubylaser on 2011-02-26
> Here's the thing. With a RAID 5, once one disk is lost anything that causes another disk to be unreadable will cost you the whole array. So you probably don't want to do anything other than either backing it up or rebuilding it. No writing. If something goes wrong while you are writing, like a power-cut or a loose cable or anything else, your whole array is toast. A degraded RAID 5 is more dangerous than no RAID at all.

This sounds like his computer may explode at any moment:)  It's not quite that dangerous.  Hopefully a user has been backing up prior to a failed disk anyways.  And the remaining disks still have the metadata on their superblocks, so you "could" lose your data on a loss of power or with a lose cable, it's more likely that you'd reboot the machine, and the array would come back up in it's previously degraded state.

---

### Post by cpressland on 2011-02-26
Hey Guys, based on this thread: [http://ubuntuforums.org/showthread.php?p=10498247#post10498247](http://ubuntuforums.org/showthread.php?p=10498247#post10498247)

I've changed my config file to look like the following:

```

DEVICE /dev/sd*
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726

```

now when the Server comes back up, the array does not come back up with it.

/dev/md0 gives a 'you must specify a partition type' error.

Any ideas guys? As Previously mentioned I want the OS on the 250GB Drive to boot, mount /dev/md0 then bring all services up like networking and transmission-daemon.

Right now it's not even attempting to bring the array online.

---

### Post by cpressland on 2011-02-26
I just brought the array up again with

mdadm --manage /dev/md0 -R

and now it's began the recovery progress from 0% again. Seriously?! Why is it starting the array rebuild from scratch on every reboot?

---

### Post by gsgleason on 2011-02-26
That is indeed weird.

I would recommend stopping the array and running backblocks on each device.  It will take a while, but it's better to know than to deal with severe data loss later on.

---

### Post by gsgleason on 2011-02-26
[http://www.issociate.de/board/post/438342/Degraded_array_on_every_reboot.html](http://www.issociate.de/board/post/438342/Degraded_array_on_every_reboot.html)

Check that out, too.

---

### Post by rubylaser on 2011-02-26
It's rebuilding everytime because your devices are changing.  I always generate my mdadm.conf file like this for generic partitions and it will use UUID's, so you don't have to worry about the order.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Put, that in place and reboot.  Unfortunately if it started rebuilding, putting a config file in place won't help.  But, this will fix the problem in the future.

---

### Post by cpressland on 2011-02-26
Okay, which is it?

DEVICE partitions
or
DEVICE /dev/sd*

Either way the array isn't working at all, this is a complete failure, I'm going to start it from scratch by purging mdadm and fdisking each disk in the array back to it's default level.

Once it's done, how do I create the array as a RAID5 and have it mount @ /home/storage/ ? and what data do I need to put in my mdadm.conf before rebooting for the first time?

---

### Post by gsgleason on 2011-02-26
Read that link I posted, man.

---

### Post by cpressland on 2011-02-26
I've gone over that, it's talking about him accidentally adding the superblock to a device instead of a partition, then he removes the superblock and that resolves the issue. Thats got nothing to do with this situation, the issue is mdadm is looking for /dev/sdb /dev/sdc /dev/sdd /dev/sde and not seeing what it wants to see, so it's assuming the hard drives have been shuffled around and rebuilding the array from scratch.

I'd use a Hardware array but for some bizarre reason Ubuntu will only see 1.4TB worth of storage space, not 8TB.

---

### Post by gsgleason on 2011-02-26
How about wiping the superblock from each disk and starting over?

stop the array, then:
sudo dd if=/dev/zero of=/dev/sdX bs=1k count=1

do that for each drive for the array

Then create the partition type fd for each one, primary partition using the whole thing, then create your array.

Also, with 4 2TB drives, you should have around 6TB usable.

I also think it would be beneficial to check each one with badblocks.

---

### Post by cpressland on 2011-02-26
Okay, I'm about to start this process, I've just done some shifting around in the BIOS to ensure it never tries to boot off of anything other than the 250GB Boot Drive and now when booting into Ubuntu the system is @ /dev/sde1 & /dev/sde2 [swap]

Am I correct in saying that the array won't work if the system decides to move back to /dev/sda1 & /dev/sda2 or at this point is this irrelevant?

---

### Post by cpressland on 2011-02-26
BTW, this is the Syntax i'm going to be using to create the RAID, is this correct?

```
madam --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

250GB Drive is back to SDA after a reboot btw.

---

### Post by YesWeCan on 2011-02-26
Giving up on the existing array? Your mdadm.conf should look like this:

```

DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726

```

---

### Post by rubylaser on 2011-02-26
You want to use partitions instead of /dev/sd*.  Also, if you are going to rebuild, you should use the metadata=1.2 on create. The new metadata format isn't bootable (you don't need this), but it supports new features.  Something like this...

```
mdadm --metadata 1.2 --create --verbose /dev/md0 --level=5 --chunk=512 --raid-devices=4 /dev/sd[bcde]1
```

I use a bigger chunk size, because it suites my data better. Also, I always update my mdadm to 3.1.4 instead of the very old 2.6.7 that comes in the Ubuntu packages.  And, when you create your filesystem, be sure to align your stride and stride_width to your chunk size.

If the disks all pass SMART tests, that's much more useful than badblocks (I assume you've checked this already.

---

### Post by cpressland on 2011-02-26
Sweet, I'll give metadata 1.2 a go, I'm just using apt-get install mdadm, it doesn't state a version. Shall I purge and update to latest build? If so, where can I get the package... and n00b alert, how do I install :P

---

### Post by cpressland on 2011-02-26
Nevermind, I've installed 3.1.4, was very easy. Just downloaded the tar, untared, make then make install. Easy, will mdadm come up automatically at boot?

Right, I've deleted the superblock of each drive except the boot drive, I've fdisked them all into single partitions with fd as the type and I've rebooted. What else is there to do? Or shall I create the array now?

---

### Post by cpressland on 2011-02-26
Okay, so, somehow it's started syncing all by itself. no /etc/mdadm/mdadm.conf exists etc and I cannot delete /dev/md0 no matter what I try. Ideas?

---

### Post by rubylaser on 2011-02-26
Good job getting the new version of mdadm.  It only has one dependency, so I just grab the mdadm from debian testing like this...
```
wget http://ftp.us.debian.org/debian/pool/main/m/mdadm/mdadm_3.1.4-1+8efb9d1_amd64.deb
dpkg -i mdadm*.deb
```

What is the output of
```
mdadm -E /dev/sdb1
``` on each of your disks.
 
If mdadm info is still there, the superblocks didn't get zeroed out.
If you want to completely remove a raid array we have to stop if first and then remove it:
```
mdadm --stop /dev/md0
mdadm --remove /dev/md0
```

Please remove the /etc/mdadm/mdadm.conf if one exists. And then zero the superblocks like this...
```
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/sdd1
mdadm --zero-superblock /dev/sde1
```

Finally, reboot.  That should completely remove everything.

---

### Post by cpressland on 2011-02-26
Okay, followed your instructions, as soon as mdadm finished creating the new array it started syncing, perfect.

Now I've rebooted and it's not come online as I'd hoped.

ARRAY /dev/md/0 metadata=1.2 spares=1 name=Galactica:0 UUID=21e8f94f:e1086c04:eabf37a3:7fdf90ec

This is in the mdadm.conf file... so I don't see why it wouldn't work. Any ideas?

---

### Post by cpressland on 2011-02-26
cat /proc/mdstat shows:


```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md0 : active raid5 sda1[0] sdd1[4] sdc1[2] sdb1[1]
      5860531200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]

unused devices: <none>
```

I think it's online... lol, so I've mkfs -t ext4 /dev/md0

Will keep ya'll posted.

---

### Post by rubylaser on 2011-02-26
That's a good start, and a valid mdadm.conf file, but I have two questions. Did you want sda in your array? And, I didn't think you where trying to have a spare but your mdadm.conf file mentions one?  It appears that one of the disks isn't synced.  What does this show?
```
mdadm --detail /dev/md0
```

And you'll want your filesystem to work with that new chunk size, so add the filesystem like this...
```
mkfs.ext4 -v -m 0 -b 4096 -E stride=128,stripe-width=384 /dev/md0
```

---

### Post by cpressland on 2011-02-26
Thanks for all your help man. Again, it's not syncing or anything, which is weird cause that's all it's been doing for the last few days :P.

Output is:

```
/dev/md0:
        Version : 1.2
  Creation Time : Sat Feb 26 23:07:16 2011
     Raid Level : raid5
     Array Size : 5860531200 (5589.04 GiB 6001.18 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sun Feb 27 00:03:57 2011
          State : clean, degraded
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Galactica:0  (local to host Galactica)
           UUID : 21e8f94f:e1086c04:eabf37a3:7fdf90ec
         Events : 12

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       4       8       49        3      spare rebuilding   /dev/sdd1
```

Deffo one drive listed as spare, can I convert it to active? If not, I really don't care now. lol.

---

### Post by cpressland on 2011-02-26
Okay, when I mount /dev/md0 the sync starts, so I guess it just doesn't begin at boot.

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sdd1[4] sdc1[2] sdb1[1]
      5860531200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  0.1% (3868244/1953510400) finish=983.2min speed=33048K/sec
      
unused devices: <none>
```

Now, last time I went through all this the system stopped booting when fstab couldn't find md0 so it stopped prompting either 'S' for Skip or 'R' for retry. Seeing as this is a headless server, how can I set it to automatically Skip if it cannot find a device? At least then I can diagnose the issue without moving the server. lol.

---

### Post by rubylaser on 2011-02-26
You could remove the mount entry from /etc/fstab for md0 and either mount the array by hand after boot, or better, make a quick script to mount it.

```
nano /etc/init.d/raidstarter
```
paste something like this, and you can add in those tweaks I gave you eariler, so they're always in place...
```
#! /bin/bash
mount -t ext4 -o defaults,noatime /dev/md0 /[COLOR="Red"]your/path_here[/COLOR]
blockdev --setra 16384 /dev/sd[bcde]

echo 1024 > /sys/block/sdb/queue/read_ahead_kb
echo 1024 > /sys/block/sdc/queue/read_ahead_kb
echo 1024 > /sys/block/sdd/queue/read_ahead_kb
echo 1024 > /sys/block/sde/queue/read_ahead_kb

echo 256 > /sys/block/sdb/queue/nr_requests
echo 256 > /sys/block/sdc/queue/nr_requests
echo 256 > /sys/block/sdd/queue/nr_requests
echo 256 > /sys/block/sde/queue/nr_requests

# Set read-ahead.
echo "Setting read-ahead to 64 MiB for /dev/md0"
blockdev --setra 65536 /dev/md0

# Set stripe-cache_size for RAID5.
echo "Setting stripe_cache_size to 16 MiB for /dev/md0"
echo 16384 > /sys/block/md0/md/stripe_cache_size

```
make it executable
```
chmod +x /etc/init.d/raidstarter
```
and add it to the runlevels
```
update-rc.d raidstarter defaults
```

That should mount the array for you and if the script fails the server will still come up and not need keyboard intervention.  And, I'm happy to help.

---

### Post by cpressland on 2011-03-04
Just wanted to say a big Thankyou to everyone who's helped out with this. After a week and a few hundred reboots and tests we're 100% Operational!

Thanks again!!!

---

