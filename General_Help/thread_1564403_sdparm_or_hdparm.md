---
title: "sdparm or hdparm?"
date: 2010-08-30
forum: General Help
---

### Post by ctsdownloads on 2010-08-30
After trying at least eight different tutorials on sdparm, I have come to the conclusion that I either have an off USB drive or something may be bug related.

Here it goes:

1) One Adaptec USB hard drive connected directly to USB 2.0 port

2) lsub shows this as 
> Bus 001 Device 008: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter

3) fdisk -l shows device as 
> /dev/sdb1

4) sudo sdparm --flexible --command=stop /dev/sdb &>/dev/null
> outputs to nothing

5) sudo sdparm --flexible --command=stop /dev/sdb
outputs to
> /dev/sdb: WDC WD20  00BB-00GUA0       0811

6) sudo sdparm -a /dev/sdb
outputs to
> /dev/sdb: WDC WD20  00BB-00GUA0       0811

As you can see, I cannot gain any power info mode information or have a chance in hell of getting the USB hard drive to spin down.

I have concluded that it must be IDE, despite showing up as sdb.

7) sudo hdparm /dev/sdb
gives me output of
> /dev/sdb:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 24321/255/63, sectors = 390721968, start = 0


So there you have it. Not asking for a free ride here, but for Pete's sake...external hard drive spin down is not the holy grail, either. Help! :)

And yes, I tried all of the above with > sdb and sdb1 .

---

### Post by ctsdownloads on 2010-08-30
So it's safe to assume that no one has USB hard drives? Come on, surely someone else has run into this? :P

---

