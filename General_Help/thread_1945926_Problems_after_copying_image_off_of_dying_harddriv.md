---
title: "Problems after copying image off of dying harddrive."
date: 2012-03-23
forum: General Help
---

### Post by UltraZone on 2012-03-23
My harddrive started making the classic predeath clicking noises a couple of weeks ago.  So I went and bout a replacement drive.  The dying one is 320gb, with 512 byte sector sizes (according to fdisk -l).  The replacement is 500gb, and apparently with 4096bytes sectors (this apparently is the new standard, right?). Anyway, I used my Apricorn disk imager (which worked perfectly when I transferred vista off the original 80gb disk to the currently dying one).  Anyway, unfortunately it appears that the damage was pretty bad, the Apricorn cloning software complained about being unable to copy data off a sector in the Ubuntu root partition (I have separate home and usr partitions, btw), and additionally at least 3 sectors of the swap partition were also too far gone for successful copying (I know, no real data loss, but an indication of the massive dump the drive is taking).  So, fast forward 10 hours of cloning, swap the drives, and all I get is the grub command prompt.  I read instructions online how to find the Ubuntu root partition and boot into it.  However, the weird thing is that grub identifies the partitions as "hd(0,msdos1)" through 9, for all of them :eek: so it thinks all partitions are windows partitions (this is strange to me to see this "msdos" in the partition name).  When I set partition 5 to boot into Ubuntu, it errors out with "system not found".  Lastly, I booted with a live USB stick and did the fdisk -l and the report shows "partition 1 does not start on on physical sector boundary" (for all partitions).

So, in conclusion, I seem to be having three problems, the disk damage to the Ubuntu partition is pretty severe, Grub was not cloned properly, and the new 500gb with 4k sector size may not be ideal to copy a system with 512byte as originally installed.

So what do you guys think? Am I just screwed?  Should I just forget about the Vista installation (I have no qualms about this honestly) and do a fresh Ubuntu install?  I also had a fedora partition that I infrequently used for testing purposes.  Should I just cut my losses now?

I should mention that the damaged disk still boots, and there is no inconsistent behavior when using Ubuntu, except for the clicking.  Should I try to isolate the damaged sectors and redo the cloning?  Your advice is deeply appreciated.  Oh yeah, since I had the forethought of separating the home and usr partitions, in theory I should just be able to copy over the data right?  Halp!

---

### Post by MisterGaribaldi on 2012-03-23
First off, why would you try to clone from a failing HDD?

Wipe the new drive and set it up from scratch, then re-integrate your data (such as you are able).

---

### Post by UltraZone on 2012-03-24
Normally speaking that's what you do to "reintegrate" your data.  How else should I do it?

---

### Post by dcstar on 2012-03-24
> **UltraZone said:**
> 
..........
I should mention that the damaged disk still boots, and there is no inconsistent behavior when using Ubuntu, except for the clicking.  Should I try to isolate the damaged sectors and redo the cloning?  Your advice is deeply appreciated.  Oh yeah, since I had the forethought of separating the home and usr partitions, in theory I should just be able to copy over the data right?  Halp!

You should use **ddrescue** and set the options to quickly retry and only make 2 or 3 attempts.

---

### Post by UltraZone on 2012-03-25
*Update*

Finally I put the new harddrive in, plugged in the Live USB and blasted all the linux partitions.  I re-arranged the /boot, /, /usr, and /home partitions, increased the Vista partition a bit then reinstalled Ubuntu.  I copied all the stuff in my home and usr folders and all is well now.  Thanks all.

---

