---
title: "Troubleshooting a REALLY Slow RAID 5"
date: 2010-12-11
forum: General Help
---

### Post by Joshua on 2010-12-11
Can anyone help me troubleshoot my RAID 5 Array?  I'm getting write speeds of 5 MB/sec and UNDER.  The platform isn't that old, so it doesn't seem like it should be going that slow.  I've tried what I know to check, but I've got lots of data on the array right now, so I haven't used some of the benchmarks that wipe data.  Everything looks good.  So I'm really at a loss.

Some details:

The server runs 10.04 with an AMD Athlon 3000 and 4 GB RAM.  I added a PCI expansion card to get 4 extra SATA ports for all the hard drives.  I think all the RAID drives are connected to that card, and I'm sure that can, technically, limit speed by quite a bit, but I still can't see it bringing writes down to less than 5 MB/s.  Sometimes less than 1MB/S.

There are two 500 GB drives arranged as "Just a Bunch of Disks" for a total of about 1TB.

Then I have that and two other 1TB drives set up as the RAID  5.  The partition is ext3 and shared via NFS to another desktop.  If I navigate there via Nautilus on the other desktop and start copying files, that's where I get the low write speed.

Where should I start looking for problems?

Edit: I should have also noted that the OS is on a separate 20GB IDE drive.  Reads and writes on that are appropriate for the drive I'm using.  And if I SSH into the server and start creating either large or small files on the array, I see the same speed problems.  So it's not a data transfer problem with the network.  It's a Gigabit network and I can watch full 1080p content from the server via NFS without any problems.

---

### Post by Joshua on 2010-12-11
Sorry for the followup, but I should probably list some of the tests I've done:

- Used dd to write about 2 GB to both the OS disk and the RAID array.  OS disk finishes in about 20 seconds, RAID 5 Array finishes in like 20 min.  Can't remember the exact time, but it was LESS THAN 1 Mb/s.
- During those writes and while I copy stuff across the network, top never reports any process above 6% CPU.
- hdparm -tT (I know this isn't the best) reports really high read speeds.

Chunk size is 64K

Filesystem block size is 4096

I appreciate any help anyone has.

---

### Post by SaturnusDJ on 2010-12-11
What do you get with hdparm -tT when testing every partition one by one?

---

### Post by Joshua on 2010-12-11
```
sudo hdparm -tT
```

Returns the following for each drive.

```
/dev/sda:
 Timing cached reads:   1328 MB in  2.00 seconds = 663.82 MB/sec
 Timing buffered disk reads:   56 MB in  3.07 seconds =  18.25 MB/sec

/dev/sdb:
 Timing cached reads:   1380 MB in  2.00 seconds = 689.88 MB/sec
 Timing buffered disk reads:  256 MB in  3.01 seconds =  85.12 MB/sec

/dev/sdc:
 Timing cached reads:   1356 MB in  2.00 seconds = 678.17 MB/sec
 Timing buffered disk reads:  270 MB in  3.02 seconds =  89.53 MB/sec

/dev/sdd:
 Timing cached reads:   1372 MB in  2.00 seconds = 686.11 MB/sec
 Timing buffered disk reads:  196 MB in  3.01 seconds =  65.22 MB/sec

/dev/sde:
 Timing cached reads:   1366 MB in  2.00 seconds = 682.58 MB/sec
 Timing buffered disk reads:  230 MB in  3.00 seconds =  76.64 MB/sec

```

/dev/sda has the OS and is an old IDE laptop drive (slow).  The rest are in the array and are SATA.

Doing the same command for the RAID devices returns:

```
/dev/md0:
 Timing cached reads:   1380 MB in  2.00 seconds = 689.58 MB/sec
 Timing buffered disk reads:  196 MB in  3.01 seconds =  65.07 MB/sec

/dev/md1:
 Timing cached reads:   1366 MB in  2.00 seconds = 682.90 MB/sec
 Timing buffered disk reads:  316 MB in  3.00 seconds = 105.31 MB/sec

```

/dev/md0 is the JBOD over sdb and sdc, and /dev/md1 is md0 with sdd and sde in the RAID 5 configuration.

---

### Post by Joshua on 2010-12-11
I just realized I ran the command on the device, not the partition (/dev/sdb rather than /dev/sdb1).  Does that make a difference?

Also, I only posted single results for all of them, but there's not much variation, and reading data isn't really a problem in practice.  Actual results from copying data FROM the array over the network are in the range reported above.  It's WRITING data to the array when things get ridiculously slow.  Are there any write tests I can do that DON'T destroy data that's already on the array?

---

### Post by SaturnusDJ on 2010-12-11
Partitions are on certain locations on the disks, if this is at the end of the disk, the speed will be slower, but that is not the point here, so no problem.

Seperated speeds look fine. The combined for /dev/md1 is a bit of a dissapointment. 133MB/s should be the max for PCI as you probably know. But not a problem either.

I don't understand why the write speeds are that low.

Did you verify the actual networkconnection speed?

---

### Post by dcstar on 2010-12-11
> **Joshua said:**
> Can anyone help me troubleshoot my RAID 5 Array?  I'm getting write speeds of 5 MB/sec and UNDER.  The platform isn't that old, so it doesn't seem like it should be going that slow.  I've tried what I know to check, but I've got lots of data on the array right now, so I haven't used some of the benchmarks that wipe data.  Everything looks good.  So I'm really at a loss.
.........

This might be worth trying:

[http://ubuntuforums.org/showthread.php?t=1625233](http://ubuntuforums.org/showthread.php?t=1625233)

---

### Post by Joshua on 2010-12-12
SaturnusDJ: 

I was getting ready to reply that I didn't think it was the network, but now I'm getting some strange results from tests that I already did.  First, is there a good way to verify the network speed?

The confusing test I did was running

```
dd count=1k bs=1M if=/dev/zero of=/foo/test.img
```

to write data on the OS drive and then on the array.  It returned something similar to the following for BOTH:

```
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 71.0087 s, 15.1 MB/s

```

The last time I did that test, it returned about 1 MB/s for the array.  Not as fast as I want but still better than it was before.  But then I went into Nautilus to transfer some files via NFS from my desktop to the server, and it was back down below 1 MB/s.

dcstar:

I'm not familiar with that patch.  Is that supposed to address general speed issues or is that specific to RAID?  I don't think I have general issues with the OS since CPU utilization is never above about 5% when I'm reading or writing data.

---

### Post by SaturnusDJ on 2010-12-12
Use 'ethtool' to see if you really are running Gbit speeds. (Also check this on the other computer.)

Maybe you can try Samba. I am no expert and anyways it is hard to see what is wrong here but maybe if Samba does work nice for you, we can say something is wrong with NFS.

A good write test might be to create a dir and mount it into your computers memory. Put a file into the dir and then write from that dir to your array.

---

### Post by dcstar on 2010-12-13
> **Joshua said:**
> 
..........
dcstar:

I'm not familiar with that patch.  Is that supposed to address general speed issues or is that specific to RAID?  I don't think I have general issues with the OS since CPU utilization is never above about 5% when I'm reading or writing data.

It makes a massive difference to systems that grind to a halt when hit with big disk I/O.

---

### Post by Joshua on 2010-12-15
Sorry for the delay on this.  I wanted to thank you guys for your help, though.

All of a sudden, I'm getting inconsistent results when I do the tests that I've been doing and haven't had time to start isolating variables.  As soon as I narrow down a configuration that gives consistent results I'll post the status and start up on troubleshooting again.

Also, I haven't tried that kernel patch (or the shorter "hack") yet, but I'll post the results of that as well if I get to it.  I'm not convinced that it will help with what I'm doing, though.  There are lots of services available on my server, but most of the they are either not used or shut down.  So when I'm just doing simple file sharing over NFS or Samba, my CPU is hardly used.  It's an Athlon 3000 with 4GB RAM, which is old, but should be more than enough for simple file sharing, right?

As long as I'm talking about the adequacy of my hardware, I thought it should be more than enough for software (mdadm-based) RAID as well.  Let me know if that's not the case.  As far as expectations, I'd be happy for a little while (until the hacker in me takes over again) with normal transfer speeds over the network (say 30 MB/s) if it were consistent.  Recently I've been getting that for short periods of time (seconds or minutes during a transfer), but most of the time it's down around 3 MB/s.  Either way, shouldn't I expect read and write operations to be FASTER with RAID than they would be with just a single disk?  Even with RAID 5 or my funky JBOD + RAID 5 setup?

Also, I've noticed two other things during the limited troubleshooting I've done since my last post.

- Read operations across the network are only about 25 MB/s - 30 MB/s.  about 1/5 or less than what I thought.  All RAID drives are SATA II but my PCI card and the mainboard ports are all SATA 1.0.
- Initial login via SSH to the server can take noticeably longer than it used to (to get to a prompt) after a restart.  Subsequent logins are almost instantaneous.  Maybe that's normal behavior since CPU and memory utilization look normal (low) any time I check them.  But perhaps there is something else going on that I can't find.

Thanks again.  Let me know if you have any thoughts, otherwise I'll post an update sometime over the next couple days.

---

### Post by rubylaser on 2010-12-15
I can only speak for myself, but my fileserver at home is an AMD Athlon 3000+ with 4GB of RAM (sound familiar? :) ).  I have a Supermicro 8 port PCI-X SATA controller. When I had 5 1TB Western Digital RE3 disks I could read/write via NFS at around 85-90MB/s.  I've since moved to RAID6 and added 3 more disks, but the speed is slightly lower due to double parity checksumming.

I would attribute your slowness to the PCI card and the JBOD 1TB array combined.  If you want to see much better performance, I would suggest ponying up the money and just buying another 1TB disk and remove the JBOD'd disks from the array.  I would expect that just buy doing that you'd see around 40 MB/s.  At that point you'd be limited by the PCI bus limiting you to 133MB/s total. So, if you wanted to push past that you'd want to move to a PCI-Express or PCI-X controller card.  Here's an hdparm from my previous 5 disk array...
```

/dev/md0:
 Timing cached reads:   7836 MB in  2.00 seconds = 3921.44 MB/sec
 Timing buffered disk reads:  954 MB in  3.00 seconds = 317.55 MB/sec

```

mdadm can be very fast :)

---

### Post by Joshua on 2010-12-15
rubylaser:  Thanks for the input.

I don't know much about the inner workings of mdadm or RAID 5, but would it be possible to test your idea by removing the JBOD part of the array and then reading and writing data to the other two?  If it sped up at that point it would seem like a clear indicator that the JBOD was slowing things down.

Or would the RAID 5 work even slower in a degraded configuration?  Also, if I write data to the array in a degraded configuration, would it have to go through a long rebuilding process when I added with the JBOD or a new 1TB drive back into the mix?

I also had a thought about the PCI bus.  I understand how I'm limited to the 133 MB/s, but shouldn't most of that equal to total rate of writing data?  Or assuming 3 drives in a RAID 5 maybe 2/3 for writing data and 1/3 for writing parity information?

Either way, I just opened the box and confirmed that all 4 disks are connected to the PCI card, but I have two open ports on the motherboard.  Do you know how much reconfiguration of mdadm it would take to move the two 1TB drives to the motherboard instead?  It seems like every time I've moved an array to a different motherboard or simply reinstalled an OS, the array doesn't just come right up because the device identifiers or disk IDs or something have changed.

---

### Post by SaturnusDJ on 2010-12-15
That would be a nice test. If I am correct degraded RAID5 is kind of similar to RAID0...so know the risk. Note that RAID5 don't uses a parity disk but spreads it over all disks.

I tried removing and re-adding a partition into a array in a virtual machine. The result is that after removing nothing happens, except having a degraded array of course and after adding again, recovery will start. So yes, it will take some time.

Partitions also have UUIDs so it must be possible to switch controllers without rebuilding. Not sure however.

Create a backup and try out.

---

### Post by rubylaser on 2010-12-16
SaturnusDJ is correct, you can easily remove a disk from an array without data loss, although you would be running in degraded mode at that point.  Also, your array would not be as fast as possible, because you just dropped the splindle count (although it should still be faster than what you're currently seeing).

When you add a new disk back in, mdadm would need to recalculate parity even if you re-added the same disk that you marked as failed.

---

### Post by jeremydt on 2011-01-07
I'm having similar issues with my RAID5 array.

Perhaps someone will see my thread and have an answer or suggestions to this or vice versa.

[http://ubuntuforums.org/showthread.php?p=10327483](http://ubuntuforums.org/showthread.php?p=10327483)

---

### Post by Joshua on 2011-01-26
I know it's been a while, but I finally got around to troubleshooting some more.  Unfortunately, I still haven't made any progress.

I moved the two 1TB drives to the mainboard.  So the two drives in JBOD are still on the PCI card.  That hasn't made any difference in the tests I've done (hdparm, dd, and copying across the network via nfs).

In the new configuration, I unplugged the JBOD and brought everything up in degraded state.  Still got the same results on those three tests.

Right now I've added the JBOD back in and it's in the process of rebuilding.

I still haven't gone out to buy a new 1TB disk to replace the JBOD.  I'm thinking that if I have to resort to that, it might be worth my time to get a new server that doesn't require the PCI card to provide enough SATA ports.  Does anyone have any other ideas that I can try?

---

### Post by Joshua on 2011-01-26
I did a little more testing with the dd command and found something interesting.

If I do:

```
dd count=1k bs=1M if=/dev/zero of=/foo/test.img
```

It will write a total of about 1.1 GB to the destination file.  Regardless of whether the destination file is on either the OS disk (a 20 GB laptop IDE drive) or the RAID array, the command reports about 15 MB/s write speed.

However, if I change the command to:

```
dd count=1k bs=1K if=/dev/zero of=/foo/test.img
```

(note the bs=1K) It will write a total of about 1 MB to the destination file.  If that file is on the OS disk, the command reports a speed jump to 134 MB/s.  But if that file is on the RAID array the command reports a speed DROP to a pitiful 282 kB/s.  YES kilo - with a k.  I can count to about 4 before it displays the output.

Anyone know what's going on here?  Is it even relevant?

---

### Post by coinmagic45 on 2011-02-09
I am having the same issue with a slightly different setup.  My desktop has a 4-disc RAID5 attached via SATA to my motherboard.  I also have a separate 1tb drive for my operating system (Ubuntu 10.04).  When I try to copy to my RAID, the write speed is typically ~2.2mb/s.  If I copy to the OS drive, I get much faster speeds.  The read speed is just fine from the RAID.  The only problem is the write speed.  Some of my specs:

Motherboard: Gigabyte GA-EP45-DS3L
CPU: Intel Core 2 Duo E8400 Wolfdale 3.0GHz
RAM: 4gb DDR2 1066
RAID drives: 4x 1.5tb Western Digital Caviar Green WD15EARS sata drives set up as ext3

I am having the same issue as the OP without the JBOD, PCI card, or network...  I have read about modifying a write cache size variable but that didn't do anything (don't have the link with me at work or I'd include a link to the article).

Any thoughts?

---

