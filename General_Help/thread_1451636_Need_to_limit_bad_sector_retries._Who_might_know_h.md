---
title: "Need to limit bad sector retries. Who might know how?"
date: 2010-04-10
forum: General Help
---

### Post by misterbk on 2010-04-10
Hello,

I am trying to use Ubuntu to transfer data from a working, but very old, 80GB PATA drive, and image it onto a new drive.  I'm using a pair of USB PATA enclosures.  Swapping them has no effect.

The old computer can still boot from and operate using the old drive, but there seem to be chunks of bad sector here and there.  (They apparently are not interfering with anything.  Probably borking some files that the system isn't using.)

In the past I have used ddrescue and/or dd for this.  I'm not new to either one, I've used both several times successfully.

**The problem:**  On Ubuntu 9.10 (x64 if that matters) the system spends SO LONG on a single bad block that the copy simply cannot progress.  I spent about 30 minutes each waiting for it to get past two bad blocks, each time having to stop the transfer and manually restart from somewhere past the bad block.  And this is on a fairly healthy, working drive.  It just threw a SMART error so I recommended my friend let me image it onto a fresh disk.

It seems like what I have going on is some sort of multi-pyramid of controllers doing retries.  ddrescue sends a read request to the kernel, on to the USB PATA bridge, on to the drive. The drive tries like 20 times and sends an error.  Kernel gets an error and tries again, so the drive tries 20 more times.  Kernel does this like 10 times or more (these numbers are all guesses) generating some 200 to 300 retry requests on the drive, each taking 2 to 6 seconds.  It's possible the USB enclosures are adding their own retries to the stack and multiplying even further.  Now ddrescue does its one allotted retry and starts another chain reaction.  I've waited quite a long time for ddrescue to go on to the next block and it never does.

At least, that's what it seems like must be happening based on the noises coming from the drive and what's happening in the system logs and the output of ddrescue.  I could easily be misunderstanding the technicals but the fact remains one bad sector is becoming an insurmountable obstacle.

To make matters worse, during the retry cycle ddrescue/dd don't respond to ctrl+C or kill.  The only way to stop the retry cycle and pick up from another spot on the disk is to unplug and replug the USB, which means I also have to re-check the drive letters to make sure the devices are still the same.


I'm aware this is a special situation but searches turn up several unanswered threads on the subject so I don't think I'm alone.  Does anyone know what's going on, how to tell the kernel not to retry, or know another forum I can go to and post there?

BTW hdparm doesn't have any helpful drive-level operations that work.  I went through everything that sounded relevant and didn't have a warning sticker on it in the man page.

---

### Post by blueridgedog on 2010-04-10
I assume you have tried  -n and --no-split in ddrescure to avoid retries?  If so, then I don't have a clue why it is trying.

---

### Post by drdos2006 on 2010-04-11
Why not try with FTP ? ( Filezilla for example ).
regards

---

### Post by misterbk on 2010-04-11
Yeah I tried all that.  Didn't seem to matter what the options were or what program was doing the read, soon as that read request went through the only thing the system would do is read that block over and over.


Know what's really interesting though?

Same drive, same enclosure, on a 32-bit Kubuntu 9.04 box, kernel 2.6.24-19-generic.

Drive pauses and makes the same noise at the same areas of the disk. (one around 100KB, one around 3MB, another around 3.2MB.)  But on this system, it makes the noise twice and continues on its merry way and the copy is flying along at an average rate of about 20MB/sec.

On the previous system, (Ubuntu 9.10 x64, kernel 2.6.31-14-generic), the noise happened repeatedly until I lost count and unplugged the USB cable.

What I don't know is, what does this mean, should I be reporting it, and where?  Does this mean Ubuntu 9.10 becomes nonfunctional if it ever reads a single bad block on its system drive?



Ubuntu 9.10 x64, kernel 2.6.31-14-generic: powerless and defeated in the face of the mighty bad block
Kubuntu 9.04 x86, kernel 2.6.24-19-generic: "Oh that one's bad I'll just move on."

---

### Post by blueridgedog on 2010-04-11
I bet it is the controller for the enclosure...not the OS.  Or, the driver/module that has been written for one set of hardware versus another.

---

### Post by misterbk on 2010-04-12
> **blueridgedog said:**
> I bet it is the controller for the enclosure...not the OS.  Or, the driver/module that has been written for one set of hardware versus another.

Then how would the same enclosure on a previous Ubuntu work perfectly?  Also I tried two different enclosures on 9.10 with the same results.

---

### Post by blueridgedog on 2010-04-12
The enclosure is connected to either a USB or eSATA interface, and those likely have different chipsets and are causing the difference (just a guess).  That could be the reason the same enclose works on one motherboard and not on another (as far as retries goes anyway).

---

### Post by dcstar on 2010-04-13
> **misterbk said:**
> 
.........
Ubuntu 9.10 x64, kernel 2.6.31-14-generic: powerless and defeated in the face of the mighty bad block
Kubuntu 9.04 x86, kernel 2.6.24-19-generic: "Oh that one's bad I'll just move on."

Then report is as a kernel bug, that is what Launchpad is for.

---

