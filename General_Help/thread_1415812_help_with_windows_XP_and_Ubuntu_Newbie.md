---
title: "help with windows XP and Ubuntu :Newbie"
date: 2010-02-25
forum: General Help
---

### Post by anshuagoel on 2010-02-25
Hi all

I am a newbie. Need some help. I am trying to install dual boot Ubuntu with Win XP SP3.

I defragmented the hard disk (Capacity 100 GB) of which windows (it shows continous files) is taking 92.5 GB and then it shows only 251 MB left for Ubuntu.

I copied almost the entire data into an external hard disk. But still it shows the hard drive with 92 GB.

My question is where is the rest of 7 GB. What do I do to get windows to vacate more from hard disk so that I can proceed with Ubuntu.

Sorry if it appears to be a very basic issue.

Thanks for all the help.

---

### Post by LintonHanes on 2010-02-25
> **anshuagoel said:**
> 
I copied almost the entire data into an external hard disk. But still it shows the hard drive with 92 GB.

..so you should have alot more space (10+gb)?

you can check (MyComputer-Properties>Advanced>) system restore, and swap/page file
..if it's default systemrestore's prolly huge (there's also the 'diskcleanup' right?)

hey, with ubuntu's partition-manager (gparted) you dont wanna squeeze it *too* close aye, windows might not like having *no* room... try and give it 3-5 gigs space I say

---

### Post by undecim on 2010-02-25
> **anshuagoel said:**
> I copied almost the entire data into an external hard disk. But still it shows the hard drive with 92 GB.

My question is where is the rest of 7 GB. What do I do to get windows to vacate more from hard disk so that I can proceed with Ubuntu.

Just copying data to an external device isn't going to free up space. You have to MOVE the data. Once the data is off the hard drive, and only on the external drive, you should have space.

As for the other 7GB, it was probably never there. HDD manufacturers usually count 1 GB as 1,000,000,000 Bytes (which should be denoted as "GiB"), as opposed to the 1,073,741,824 that GB really means (look at that: about 0.07GB difference per GiB)

---

### Post by Mark Phelps on 2010-02-25
> **anshuagoel said:**
> ... then it shows only 251 MB left for Ubuntu.
That's a very small amount of space -- small enough that if it gets any smaller, you're liable to encounter problems booting WinXP.

> I copied almost the entire data into an external hard disk. But still it shows the hard drive with 92 GB.

What do I do to get windows to vacate more from hard disk so that I can proceed with Ubuntu.

Since you've already copied these, you need to go through and decide which ones to delete.  Try to free up about 10GB of room for Ubuntu.  Also, be sure to empty the Recycle Bin -- the space does not get freed up until you do that (unless you do direct deletes instead).

---

### Post by PoHandle on 2010-02-25
I agree with the previous posts that instruct you to delete the original files that you have copied to your external HDD.  After that, I'd recommend that you use PageDefrag ([http://technet.microsoft.com/en-us/sysinternals/bb897426.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897426.aspx)) to defrag your pagefile as well as other things that the regular defragmenter won't get.  After that, run the regular defragger 2 or 3 times to ensure you aren't going to lose any data near the end of the partition when you shrink it.

---

### Post by anshuagoel on 2010-03-05
Thanks guys - very helpful indeed.

:KS

---

