---
title: "Write Speed Problem with Hard Disk and/or Partitions"
date: 2010-05-10
forum: General Help
---

### Post by SomeOne77 on 2010-05-10
Hi,
I have what seems to be a hard disk Write speed problems with my first hard drive. Timing the cp command of a 700 Meg file takes about 8 secs from disk 2 to 3 but takes 25 minutes from disk 2 to disk 1.  
Here are the details

Kubuntu 9.04 (Kernel 2.6.28-15-generic)
Hard Disk 1 : /dev/sda (WDC WD2500KS-00MJB0)
Partitioned 
/dev/sda1 ext3 /          10 Gigs
/dev/sda2 extended    222 Gigs
/dev/sda5 linux-swap   2 Gigs
/dev/sda6 ext /home 220 Gigs

Hard Disk 2 : /dev/sdb (WDC WD2500AAKS-00F0A0)
Partitioned :
/dev/sdb1 ntfs 16 gigs
/dev/sdb2 xfs /home/eric/data_drive 216 Gigs

Hard Disk 2 : /dev/sdc (ST3500320AS)
Partitioned:
/dev/sdc1 xfs /home/eric/data_drive2 465 Gigs


By doing 'time cp ...sdb1/test.avi ...sdc1' takes about 8 seconds and same vice-versa
the command 'time cp ...sdb1/test.avi ...sdb1/test1.avi takes about 11 seconds and the same holds true if sdc1 is used

But copy sdb1 or sdc1/test.avi to either sda1 or sda6 and it takes 25 minutes.  Same problem if I copy from the same drive partition (sda)

I have booted a livecd Knoppix 6.2 and the same problems happens.. So safe to say it's not Kubuntu.

I have done searches on the internet and did not find a solution.

The only thing that is left to do is backup and reformat the partitions as XFS and try again.

Edit :
I also did a full smartcontrol Extended test and no errors.  Checked all the various logs and nothing found

Comments, ideas ???

Thanks!

---

### Post by kidders on 2010-05-11
Hi there,

If I were you, the next thing I would do is try to rule out filesystem issues (eg a performance bottleneck due to severe fragmentation), but I'm guessing you've already thought of that, since you mentioned backing up & reformatting. I'd be interested to see if there's still a significant performance difference between the drives.

If /dev/sda has any unallocated space on it, you could create a temporary partition (ie with no filesystem in it) and use dd to dump a couple of hundred megabytes of garbage into it. Comparing the time that takes with a similar test on one of your other disks would be an easy, non-destructive way to get a clearer picture of what's going on. For example ...```
dd if=/dev/urandom of=/dev/sda7 bs=4096 count=50000
dd if=/dev/urandom of=/dev/sdb3 bs=4096 count=50000
```

I hope that helps.

---

### Post by wirelessmonkey on 2010-05-11
Run iotop, and see if you have something(s) doing significant i/o on sda, besides your cp.

---

### Post by SomeOne77 on 2010-05-16
Hi
@Kidders

Thanks for the tip. But I don't have any  unallocated space and don't feel comfortable doing a resize.

But what you said got me thinking.
I booted a live CD again and formatted my swap partition to xfs and did the cp test again .

Well it's worse that on the ext3 partitions.
It took 75 minutes from sdc1 to sda5 and 87 minutes from sda5 to sda5

I am now thinking of doing a full backup and then downloading and running the diagnostic Boot CD from the vendor.

@wirelessmonkey.

I did check iotop and there is nothing else running (when in livecd mode)..

I did notice however that it does IO in burst... Not continous.  Also seemed to have copied the first 125 Megs rather quickly and the rest took forever

Thanks all for the tips.  Any more ideas ?

Thanks!

---

### Post by wirelessmonkey on 2010-05-16
I may be wrong, but I don't think you're supposed to have a filesystem on swap...

---

### Post by SomeOne77 on 2010-05-17
Yes you are right.. .  I just did not explain myself correctly

I did a swapoff and formatted my swap partition and then formatted it to xfs to do the test.

Thanks!

---

### Post by wirelessmonkey on 2010-05-17
For kicks, what's the output of
```
 hdparm -tT /dev/sda

```?

---

### Post by SomeOne77 on 2010-05-17
Hi
Here is the output of all the drives.. Like I said.. Seems to be a write problem


/dev/sda:
 Timing cached reads:   1642 MB in  2.00 seconds = 820.94 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.85 MB/sec

/dev/sdb:
 Timing cached reads:   1600 MB in  2.00 seconds = 800.52 MB/sec
 Timing buffered disk reads:  336 MB in  3.00 seconds = 111.98 MB/sec

/dev/sdc:
 Timing cached reads:   1584 MB in  2.00 seconds = 792.40 MB/sec
 Timing buffered disk reads:  278 MB in  3.01 seconds =  92.51 MB/sec

---

### Post by kidders on 2010-05-18
> **SomeOne77 said:**
> Timing buffered disk reads:  186 MB in  3.01 seconds =  61.85

I can't come up with a sensible explanation for that. :-( As far as I can tell, you've ruled out everything except ...

[LIST]
[*]A faulty cable or I/O interface. Unlikely, imo ... slow writing is far too specific a problem to be caused by a fault.
[*]Something bizarre about your motherboard that slows down one of the I/O interfaces.
[*]A broken disk.
[/LIST]

I'd be interested to see what happens if you swap the disks at /dev/sda and /dev/sdb around ... ie whether the performance problem follows the disk to /dev/sdb, or stays where it is. Other things to check ...

[LIST]
[*]Are you certain the performance-related specs of /dev/sdb and /dev/sda are the same (eg the buffers are the same size)?
[*]What motherboard do you have?
[/LIST]

---

