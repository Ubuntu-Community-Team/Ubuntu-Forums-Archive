---
title: "How to get ext4??"
date: 2009-08-11
forum: General Help
---

### Post by dtrot55 on 2009-08-11
I just installed a fresh copy of 9.04 from the install cd and I was not given an option to choose ext4.  I thought that 9.04 came with this option?  I wasn't given any option it was chose partition and it went.  Any ideas?

---

### Post by Maheriano on 2009-08-11
You need to manually specify the partitions. If you let it partition automatically it will do EXT3.

---

### Post by dtrot55 on 2009-08-11
So when i reformat chose manual and then pick ext4 and give it the whole hard drive?

---

### Post by Maheriano on 2009-08-12
> **dtrot55 said:**
> So when i reformat chose manual and then pick ext4 and give it the whole hard drive?
You could do that but it'd be smarter to split your partitions. I have 15 gigs for  the / directory to install applications and settings in, 4 gigs for SWAP because I have 2 gigs of RAM, and then I have about 980 gigs set for my /home directory to download stuff in. This way if I need to reinstall for any reason, I can reinstall into the / directory without losing my files in the /home directory.

If you use the entire partition and need to reinstall, you lose everything. But yes, you can do that.

---

### Post by dcstar on 2009-08-12
> **dtrot55 said:**
> I just installed a fresh copy of 9.04 from the install cd and I was not given an option to choose ext4.  I thought that 9.04 came with this option?  I wasn't given any option it was chose partition and it went.  Any ideas?

Given that EXT4 still has serious issues, I would not choose it (if I had known of these issues before I did my own 9.04 install, I would not be using it now myself).

Wait until it is more mature and things like the resize bug are fixed (look in the 9.04 release notes).

---

### Post by Arup on 2009-08-12
I have two PCs with ext4 and from the day of install, I haven't got a single issue, one of them has seen two dirty shutdowns and even then there was no data loss etc.

---

### Post by credobyte on 2009-08-12
Manual partitioning will let you choose between file systems, however, I wouldn't go for ext4 .. it's quite unstable at the moment ( tried it twice @ will never try again until it'll be officially marked as stable/default ).

---

### Post by dtrot55 on 2009-08-12
I didn't know you could do it like that...what would you reccomend for a 60 gig hard drive?

---

### Post by nikhilk on 2009-08-12
> **dtrot55 said:**
> I didn't know you could do it like that...what would you reccomend for a 60 gig hard drive?

Give about 10-15 GB for the / partition.
The rule of thumb is to have swap partition twice the amount of RAM you have. So if you have 1GB RAM use a 2GB swap partition etc.
Leave the rest to your /home partition where you should save all your data (documents, photos, videos, games, downloads etc.)

---

### Post by dtrot55 on 2009-08-12
Will do..i need to format anyways...thanks for the info...I have read that the ext4 helps some with the older processors...so hopefully its true

---

### Post by nikhilk on 2009-08-12
> **dtrot55 said:**
> Will do..i need to format anyways...thanks for the info...I have read that the ext4 helps some with the older processors...so hopefully its true

Disclaimer: I have never used a ext4 formatted partition

From what I have heard from others: ext4 offers some really nice performance improvements over ext3. I won't say ext4 is too buggy for everyday use but it is a bit fragile and has not matured yet.

So if possible, try ext4 on a test machine or on your actual machine with non-critical data that be can restored even if completely wiped out. See the performance and stability for yourself and then decide; that IMO is always the best way.

---

### Post by Simian Man on 2009-08-12
ext4 is very stable, I have been using it for 10 months or so now with no issues.

---

### Post by Maheriano on 2009-08-12
Well I actually moved to EXT4 because my old EXT3 filesystem got corrupted. So for me I find EXT4 more stable so far, I've been using it on my laptop and desktop for 4 months.

---

### Post by Arup on 2009-08-12
If you put the entire partition in ext 4, Ubuntu boots up way quicker as well, thats another added benefit of ext4, also file transfer, opening folders is quicker as well.

---

### Post by RavanH on 2009-08-12
Ok, here another user experience with Ext4 just to warn you: 

Since upgrading to Jaunty and switching all my ext3 partitions to ext4 on two machines (one 64bit and one 32bit) I get many sudden lock-ups :( Sure I get a much faster boot time but hey, that does not compensate for the many reboots I have to do now!

Sometimes a whole day without issues, then others where I will need to reboot three or four times a day to continue my work (which gets partly lost during the process). I moved to Ubuntu/Linux because of its stability (instead of Windoze) but now I am back to where I came from...

I regret VERY much having moved to ext4 but since it is a lot of work (make a complete backup of home partition and reïnstalling jaunty  and restoring all files, mail and settings from the backup seems daunting to me) to revert to ext3 I am hoping there will be stable ext4 support VERY soon... [-o< 

My advice: stick with ext3 until ext4 becomes default (if ever) !

---

### Post by dtrot55 on 2009-08-12
Well this is on my laptop running a pent m 2.0ghz processer with 1 gig of ram so any performance i can get im taking...this really isn't a huge deal to me if things get screwy...so far i think ive had one little blip that logged me out but other than that things are running fine.  But yeah I won't do this on my main computer.

---

