---
title: "Hard drive failure?!??!!"
date: 2010-02-11
forum: General Help
---

### Post by nickajeglin on 2010-02-11
I've been running Karmic happily for several weeks now. Today when I came home from work I was greeted by a notification informing me that me external hard drive may be failing due to the fact that it has many bad sectors. I am disinclined to believe this, due to the fact that the hard drive is less than 2 months old. It is a 1 terabyte seagate external drive. Does anyone know whether this is a bug in Karmic, or should I be backing up my data asap?

---

### Post by Richard1979 on 2010-02-11
"*The only thing better than a fresh backup* *is a warm bacon sandwich with  a hot cup of tea*" - me

Backup in case.
Then run a manual fsck on the disk in question.

To schedule a fsck on a given partition at next reboot, create a file called forcefsck on the root of the partition.

---

### Post by samantha_ on 2010-02-11
> **nickajeglin said:**
> I've been running Karmic happily for several weeks now. Today when I came home from work I was greeted by a notification informing me that me external hard drive may be failing due to the fact that it has many bad sectors. I am disinclined to believe this, due to the fact that the hard drive is less than 2 months old. It is a 1 terabyte seagate external drive. Does anyone know whether this is a bug in Karmic, or should I be backing up my data asap?

Welcome to the wonderful world of bug tracking. [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by john newbuntu on 2010-02-12
Seagate might have a utility that you can boot from and check the disk ([http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)).  Use that to double check what palimpset says.  I agree palimpset might have false positives. But what if it is right?
Remember the golden rule - always backup your data.
Also, fsck and e2fsck only check the consistency of files and not the condition of the disk.

---

### Post by Grenage on 2010-02-12
> I am disinclined to believe this, due to the fact that the hard drive is less than 2 months old

There are reasons to disbelieve that the drive is really failing, but age is not one of them.  Hard drives are mechanical and very prone to failure, still at least they have three-year warranties if it does.

---

### Post by nickajeglin on 2010-02-12
Thanks for the replies everyone, I'll check the drive using the seagate utility, and if it's a false positive, should I add my confirmation to the bug at launchpad?

---

### Post by Grenage on 2010-02-12
> **nickajeglin said:**
> Thanks for the replies everyone, I'll check the drive using the seagate utility, and if it's a false positive, should I add my confirmation to the bug at launchpad?

You can never have too much data, so aye.

---

### Post by Sentience on 2010-02-26
Why is the community not acknowledging the fact that the Karmic Koala seems to be associated with Harddrive failure? While the problem is arguably in the firmware of the harddrive itself (Technically), these hard drive failures are not happening on the same hardware when running windows or OSX.

I thought this issue was fixed, but I just lost another harddrive.

---

### Post by Grenage on 2010-02-26
Because there is nothing that indicates a problem?  A handful of paranoid people carrying bad luck does not constitute evidence.

---

