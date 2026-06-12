---
title: "Looking for help with unusual disk behavior during ddrescue"
date: 2011-04-18
forum: General Help
---

### Post by fatherted on 2011-04-18
Greetings, all - 

I posted a couple of days ago in a relatively hopeful mood, but I'm now hoping someone will have a suggestion to reduce or eliminate a particular behavior that's happening when I'm trying to recover data from a failed drive. 

Basically, no matter what utility I use, the drive goes entirely offline after somewhere from a few seconds to a minute or two of successfully recovering data. Sometimes it bombs after doing one or two sectors, other times I'll get several hundred MB before it dies. 

It *appears* that what's happening is that the drive gives so many read errors that the system just stops paying attention to it. 

Once it stops transferring data, it won't even show up on fdisk. There are large numbers of errors in syslog and dmesg. 

I obviously know that the chances of getting much data off it are minimal, but I'd like to get what I can. 

I don't know what's making the disk drop offline, exactly, and I don't really know how to find out. 

Does anyone have a suggestion as to where to start looking? 

Below is a segment of /var/log/messages showing what happens - this repeats a few hundred times and then the drive goes away. 


```
Apr 18 21:36:35 Hal kernel: [ 1859.920258] sd 6:0:0:0: [sdf] Unhandled error code
Apr 18 21:36:35 Hal kernel: [ 1859.920260] sd 6:0:0:0: [sdf] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Apr 18 21:36:35 Hal kernel: [ 1859.920262] sd 6:0:0:0: [sdf] CDB: Read(10): 28 00 00 98 77 da 00 00 01 00
```

And, lastly, I've verified that the data recovered thus far is actually good. I have one partition done and another about half done, and the recovery images mount up properly and are readable with good data. Unfortunately, the two partitions in question amount to just a few GB out of 250.

---

### Post by Hedgehog1 on 2011-04-19
This doesn't sound good.

The only option I can come up with is to start at the other end of the disk:

> `-R'
`--reverse'
Reverse direction of all copy operations. This means the copy of the non-tried blocks, splitting and retrying are run backwards, while trimming is run forwards. 

If the errors are because of damaged surface on the drive, this will help.  If the errors are because of failing/overheating electronics on the drive, this will not help.

Sorry I don't have more.


***The Hedge***

:KS

---

### Post by fatherted on 2011-04-19
Thanks for the response. 

I tried reverse and it seems to have the same behavior - works great for a few MB, then dies completely.

I think it's most likely firmware related. 

I'm assuming this because, if I wait for it to die, it'll continue skipping all blocks as "bad" infinitely. 

But, if I kill the dd_rescue (or ddrescue, which is what I've been using primarily), unplug SATA power, replug SATA power, then resume from a few blocks *before* the point where I quit - it transfers fine, no errors. 

This leads me to believe it's controller-related. 

I have an identical make/model drive here which I'm trying to perform the recovery to (before I knew how bad this one was, I thought I could just image it directly to a direct-replacement drive and call it a day). I tried swapping controller boards, but neither drive would show up at all, they wouldn't even show in the BIOS.  I'm guessing this is because of different firmware versions, but I can't locate a download link for any firmware version that I could use to make them match. 

Here's what I get: 

```


root@Hal:~# smartctl -a /dev/sdf | grep -B 3 irmw
Model Family:     Seagate Momentus 5400.6 series
Device Model:     ST9250315AS
Serial Number:    5VCDRYK6
Firmware Version: D003DEM1

root@Hal:~# smartctl -a /dev/sde | grep -B 3 irmw
Model Family:     Seagate Momentus 5400.6 series
Device Model:     ST9250315AS
Serial Number:    6VCPSZ7B
Firmware Version: 0001SDM1

```

If anyone has a link to a flash tool and a firmware versino for these drives, I don't have much to lose at this point.  If it matters, sdf is the bad one.

---

### Post by Hedgehog1 on 2011-04-19
> **fatherted said:**
> I have an identical make/model drive here which I'm trying to perform the recovery to (before I knew how bad this one was, I thought I could just image it directly to a direct-replacement drive and call it a day).

'Call it a day' is how it usually goes, actually.  It is only in really bad failures you see this painful behaviour.

> **fatherted said:**
> I tried swapping controller boards, but neither drive would show up at all, they wouldn't even show in the BIOS. ... This leads me to believe it's controller-related. 

Is is possible to move your rescue attempt to a different computer with SATA on the mother board?  Alternately, could you move the bad drive to a SATA/USB connection and read it from there?  *Trying to bypass the current controller somehow...*


***The Hedge***

:KS

---

### Post by fatherted on 2011-04-20
Yeah... I was quite surprised to have so much trouble with this one. I do recoveries on a lot of failed hard drives at work on almost a daily basis that have been in terrible environments and running 24/7 for years - this is a relatively new laptop drive that sustained a *minor* shock (not even adequate to register on the G-sensor in smartctl, near as I can tell) and it's being a giant pain in the rear. 

Anyway, I have tried 4 different controllers. My motherboard has 3 - an Intel ICH8, SiI 3132, and Jmicron JMB362. The Intel doesn't recognize the drive at all - there aren't even any errors, let alone a readable disk. The SiI and the Jmicron both seem to behave about the same, but the Jmicron might be a bit better. I also tried an MSI board with some unknown integrated controller at my office and it wouldn't see the drive at all either. The inconsistent behavior is what keeps stringing me along - I keep thinking that if I could just find a controller that didn't occasionally drop the link, I could just let it run. 

I don't have access to an external USB case that supports SATA drives, but might be able to borrow one from a friend - we'll see.

---

### Post by fatherted on 2011-04-20
Sorry to bump my own post, but it occurs to me that I might be able to automate this entire process if I knew how to force a hard reset of the SATA link? 

Not sure if that would actually work. 

Unplugging the SATA data cable and re-connecting it does not cause the drive to become recognized again - only disconnecting the power and reconnecting it. 

Nevertheless, if I knew how to force re-detection it might be worth a shot?

---

### Post by dcstar on 2011-04-20
> **fatherted said:**
> 
........
Nevertheless, if I knew how to force re-detection it might be worth a shot?

```
gksudo partprobe
```

---

### Post by fatherted on 2011-04-26
Ah, that would've been handy to try. 

Unfortunately, since I last posted, the drive ceased being recognized by the BIOS entirely.  I tried swapping the heads and controller from my identical spare drive but managed to sneeze and drop the new head >.<  I'm pretty sure the chances of me being able to straighten the heads out to a usable degree with tweezers are minimal at best. 

I won't say it's the stupidest way to destroy a drive I've ever heard of, but it's gotta be up there. 

I'm not sure yet if I'll bite the bullet and try another swap.  The spare drive can be had for only about $40. We'll see if the person whose data it is wants to pay for one and try again (I'll eat the cost of the first spare since I borked it up, of course). 

Thanks for the help and suggestions, fellas.

---

