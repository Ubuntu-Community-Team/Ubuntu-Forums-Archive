---
title: "bad sectors on HDD"
date: 2010-03-26
forum: General Help
---

### Post by seth elohim on 2010-03-26
Twice now on different computers i have had Ubuntu 9.10 detect bad sectors on hard drives. I have just a few questions about this: Is it strictly always a physical problem, or will a reformat sometimes take care of it? Is it relatively safe to use a drive with bad sectors, or is data loss an eminent outcome? What generally causes a drive to go bad, age? Rough handling? Perhaps poorly coded software? This is not an emergency question, but it is something that will enrich my general I.T. knowledge and help me fix my friends computers with more assurance in the future. Any insight will be greatly appreciated, and pardon my ignorance if it is a no brainer question.

---

### Post by coolcaseley67 on 2010-03-26
Hi 
fill the gap : 
- what is your hard drive ??
your q&A :
_Is it strictly always a physical problem ?_
-not always  depending , how old and what on the drive and the format .
_will a reformat sometimes take care of it ?_
- some time's r ember  you can never fully remove data .  
- if the problem keeps coming back , your hard drive need replacing .
_Is it relatively safe to use a drive with bad sectors, or is data loss  an eminent outcome?_
-in Linux most like ubuntu use EXT4 file system Google and big company's use it and to fix  go in to the recovery mode , chose repair( hard drive check ) 
- in windows data loss will be highly likely. 
_What generally causes a drive to go bad, age_? 
- age is the most likely !!.

hope it helps

---

### Post by seth elohim on 2010-03-26
thanks for the response. Actually I have gotten this message on two different drives. One was a western digital 100 gig IDE. and the other was a 250gig laptop drive that was in a Toshiba satellite, but i dont remember the make. The file structure was EXT4 because they were both after a fresh karmic install. Thanks again for your time.

---

### Post by QIII on 2010-03-26
There was an annoying bug in a fresh Karmic install causing false reports of disk problems.

Have you updated?  That cleared it up for me.

---

### Post by seth elohim on 2010-03-26
No, i have been using the same 9.10 disk forever. But i dont always get the error, and i have done several installs with this disk. (I have converted my share of unhappy windows users). Maybe it is time i get a new ISO....

---

### Post by prodigy_ on 2010-03-26
> **seth elohim said:**
> Twice now on different computers i have had Ubuntu 9.10 detect bad sectors on hard drives.
It may be just a false positive due to [an outstanding bug in libatasmart](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136).

> **seth elohim said:**
> Is it strictly always a physical problem
Not strictly always, but practically always.

> **seth elohim said:**
> Is it relatively safe to use a drive with bad sectors
The short answer is "no", it isn't safe. 

> **seth elohim said:**
> What generally causes a drive to go bad, age? Rough handling?
Yeah, but you should understand that not all HDDs are made equal. A recent example is Seagate 7200.11 series. Incredibly low quality and a very high rate of failures within 8-10 months of use.

> **seth elohim said:**
> Any insight will be greatly appreciated
Always have an up-to-date backup of everything you think is at least somewhat valuable. :-)

---

### Post by QIII on 2010-03-26
It wouldn't hurt to use a dedicated disk health application, just to be  sure.

What are the odds that two computers would have errors?  I suppose it  depends somewhat on the age of the machines.

Age and handling are frequent culprits.

If you handle a disk roughly, you can bang the heads on the platters and do actual physical damage.

Brand of disk can also be implicated.

Software is an outside chance, but not terribly common.

---

### Post by QIII on 2010-03-26
Funny you should mention the Seagate 7200.11 series.  The problem there was often a particular firmware issue where the firmware went into a continuous loop.

A few weeks ago I was able to unbrick one with a Nokia data cable and a few commands in gtkterm.

---

### Post by prodigy_ on 2010-03-26
> **QIII said:**
> Funny you should mention the Seagate 7200.11 series.  The problem there was often a particular firmware issue where the firmware went into a continuous loop.
SD15 wasn't the only problem with 7200.11. Moreover, if I'm to trust the customer reviews of 7200.12, the situation persists.

Seagate has even [changed their warranty terms](http://news.softpedia.com/news/Seagate-Lower-Warranty-Time-From-5-to-3-Years-99912.shtml). If that's not a sign of trouble, I don't know what is...

---

### Post by QIII on 2010-03-26
I did say "often" ;).

And Seagate's Customer Satisfaction approach is "Here's a new drive.  Sorry about your data."

I suspect they refurbish your drive and sell it with a large lot to Geeks.com.

Oh... By the way.  If it was an OEM component (which is marked on the drive), the answer is "Too bad.  So sad.  Talk to Gateway."

---

### Post by seth elohim on 2010-03-26
wow, i am learning a lot from this thread
:)

---

