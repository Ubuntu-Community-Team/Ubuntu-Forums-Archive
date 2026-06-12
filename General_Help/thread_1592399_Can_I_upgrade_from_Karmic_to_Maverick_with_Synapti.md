---
title: "Can I upgrade from Karmic to Maverick with Synaptic?"
date: 2010-10-10
forum: General Help
---

### Post by bomgd3 on 2010-10-10
I had lots of problems with 10.04 (see the random freezing thread...) so I went back to 9.10.  Now I've heard that 10.10 has addressed many of the issues.  However, I don't want to go through the trouble/uncertainty of upgrading with a new install and want to do it through Synaptic.  I don't see this option--it only gives me the option to upgrade to 10.04.1.  Is it possible to go from Karmic to Maverick through Synaptic?

---

### Post by mörgæs on 2010-10-10
> **bomgd3 said:**
> I don't want to go through the trouble/uncertainty of upgrading with a new install

An upgrade through Update Manager is far riskier than a fresh install.

One can not go from 9.10 to 10.10, and by all means, test 10.10 on your machine first before considering this release. 

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by bomgd3 on 2010-10-10
Okay--how exactly do I install while maintaining the correct mount points?  This has never been really clear to me.  I have my Home on a separate partition from my other partitions, so should I just delete all of the other partitions and re-mount Home in the installer?  Are there other things I should keep?

---

### Post by cgroza on 2010-10-10
You can in 2 steps. 1. Upgrade to Lucid. 2. Upgrade to Maverick. But I suggest doing a fresh install with Maverick because if you do it the long way you will download about 1.8 GB of software + the risk of the upgrade going wrong.

---

### Post by bomgd3 on 2010-10-10
Thanks!  But can I just re-mount my /home and delete all of my other partitions during the clean install?  The only software of any real importance I have is Matlab--the rest basically came with Ubuntu.  Matlab is on the /home partition.

---

### Post by efflandt on 2010-10-10
Use the Advanced mode of the partitioning part to chose (or change) which partitions you use for / or anything else, format those (other than any data or Windows partitions you want to keep), but do NOT format your /home partition.

No need to do anything to use existing swap, because it will pick that up automatically.

Sometimes you never know when something is going to work or not.  I had all sorts of problems with 9.10 on a low end laptop from 2004 (dropped keys, delayed/jumpy mousepad, failure to resume from suspend or hibernate).  But all that worked fine in 10.04 (with just **nomodeset** kernel boot parameter to disable kms).

---

### Post by 23dornot23d on 2010-10-10
If the /home is on a separate partition that should work ok.

If you want to post a screenshot of gparted of the drive layout ..... it may help .....

Just to see if there may be any problems ..... and it should confirm if the drive layout is ok .

---

### Post by bomgd3 on 2010-10-10
Here's a screenshot

---

### Post by migs73 on 2010-10-10
My partition layout was much the same. I halved the size of my root partition and made a new one with the remainder. I then installed 10.10 into that. I still have 10.04 that I have the option to boot into as well. Once I get 10.10 upto speed (everything I need working) then I can wipe it (10.04). I'll keep the partition for 11.04!

---

### Post by 23dornot23d on 2010-10-10
> **migs73 said:**
> My partition layout was much the same. I halved the size of my root partition and made a new one with the remainder. I then installed 10.10 into that. I still have 10.04 that I have the option to boot into as well. Once I get 10.10 upto speed (everything I need working) then I can wipe it (10.04). I'll keep the partition for 11.04!


This is a good idea ..... and you are not burning your bridges if you do it this way ....

You end up Dual Boot between 10.04 and 10.10 ...... using the same /home .....

I would do this if it were mine ...... resize sda6 to 40 gig ..... and you will have a clean space for 10.10 which will be 40 Gig .....

---

