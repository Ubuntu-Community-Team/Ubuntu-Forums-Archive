---
title: "Will mounting a SATA drive to an IDE decrease the performance of the SATA drive?"
date: 2010-11-16
forum: General Help
---

### Post by conft on 2010-11-16
Hi all, first post! The title says it all.
I've installed ubuntu server 10.10 on an IDE drive and mounted 2 SATA drives in /drives folder. I find the network transfer speed from/to another computer pretty slow, could it be because of the IDE drives limited speed?

Thanks!

---

### Post by krismatth3 on 2010-11-16
Well, you could test that theory by doing

```

hdparm -tT /dev/hda 

```

(replace /dev/hda with the actual IDE hard disk device)

---

### Post by conft on 2010-11-16
Thank you for the quick reply! My theory appears to be wrong. Here is the output:

/dev/sdc:
 Timing cached reads:   770 MB in  2.00 seconds = 384.75 MB/sec
 Timing buffered disk reads:  168 MB in  3.03 seconds =  55.53 MB/sec

/dev/sda:
 Timing cached reads:   816 MB in  2.00 seconds = 408.05 MB/sec
 Timing buffered disk reads:  146 MB in  3.08 seconds =  47.36 MB/sec

/dev/sdb:
 Timing cached reads:   868 MB in  2.00 seconds = 433.62 MB/sec
 Timing buffered disk reads:  372 MB in  3.01 seconds = 123.50 MB/sec

/dev/sdd:
 Timing cached reads:   786 MB in  2.00 seconds = 393.10 MB/sec
 Timing buffered disk reads:  144 MB in  3.01 seconds =  47.89 MB/sec

/dev/sde:
 Timing cached reads:   848 MB in  2.00 seconds = 423.90 MB/sec
 Timing buffered disk reads:   80 MB in  3.00 seconds =  26.63 MB/sec

sda and sdb are SATA drives
sdc and sdd are IDE drives (ubuntu is installed on sdc)
sde is an IDE laptop drive

I suppose it's SAMBA config then...

Thank you

---

### Post by tgalati4 on 2010-11-16
SAMBA is not known for its speed, but for its compatibility.  If these transfers are linux-to-linux, then you can use fuse (man fusermount) and you might get an increase in throughput.  Also your network comes into play (100 Mbit/sec vs 1 Gbit/sec) and your routers etc.  Getting high quality network cards and routers can improve performance.  Remember that a 100 Mbit/sec ethernet card will only be able to sling data at 12.5 MBytes/sec (roughly 1/10 the speed of an internal IDE bus).  Don't expect to stream those High Def videos in real time.

IDE taps out at ~133 MB/sec, SATA1 is ~150 MB/sec, SATA2 is ~300 MB/sec.  So unless your platters can throw data faster than 133 MB/sec, you may not notice a performance hit between IDE and SATA.  Sometimes the BIOS will declock the data bus to support IDE&SATA operation.  That is why the BIOS asks if you have IDE drives connected--it shuts off the IDE controller otherwise.  As a general rule, SATA-only operation will be faster within a given machine, but over the network, due to latency, you may not know the difference.

---

### Post by conft on 2010-11-17
I'm using gigabit net with a cisco gigabit switch, CAT6 cables and the drives are configured in RAID 0. I used to have XP installed on this machine, than the transfer speed was around 55-65MB/s. Now I'm getting 30MB while copying from the linux box and 20MB while copying to the box (from XP). I've tried to install the network card driver but so far no success.
I think I'm gona open a new thread regarding that issue.

Thanks for the input guys!

---

