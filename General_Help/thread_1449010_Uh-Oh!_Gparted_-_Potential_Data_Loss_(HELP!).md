---
title: "Uh-Oh! Gparted - Potential Data Loss (HELP!)"
date: 2010-04-07
forum: General Help
---

### Post by mattlach on 2010-04-07
Hey all,

I was resizing a large ext3 partition last night (830Gb to 880Gb) in Gparted.

I'm in the process of reinstalling operating systems and moving stuff around.  I read there was a problem with more recent versions of Gparted (specifically when it comes to NTFS partitions) so I opted to use my Ubuntu 9.04 live CD for this purpose.

The queue looked something like this:

- Check file system
- move partition to the left
- grow file system
- Check file system

I started it, saw that it was going to take 2+ hours and decided to go to bed and finish it off this morning.

The problem:
When I woke up I expected to find the batch job complete, but it wasn't.   It was stuck on the final "check file system". When I look at look at running processes e2fschk isn't even running, so I'm assuming something happened, causing the child process to terminate, and Gparted didn't notice and is just sitting there waiting for it to complete (which it never will).

Since it already completed moving stuff, and was just stalled on the final file system check, am I safe?   Could I just quit it, and re-run a fschk manually without data loss?

I haven't canceled Gparted yet just in case something arises that I might have to do before doing so.

The only part that concerns me is that if I run an fdisk -l it still displays the old partition table from before I moved the partition.  I'm wondering if this is because Gparted has the drive locked during its operations...

Any help would be appreciated.  Most of the stuff on this partition is replaceable, excpet for the some 5 years of pictures that I don't have backups of.

(I know they say you are supposed to back up your partitions before resizing them, but the truth is, if I had the means to pack up 900gb of data, I wouldn't need to use Gparted, I'd just back it up, manually change the partitions, and restore it again...)

Please help!

Thanks,
Matt

---

### Post by clhsharky on 2010-04-07
HI Matt

I feel for you. This i mostly a bump to get you back on top again. You might get faster results IRC #ubuntu and have you looked at Gparted forum.
[http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/)

Sharky

---

### Post by mattlach on 2010-04-07
> **clhsharky said:**
> HI Matt

I feel for you. This i mostly a bump to get you back on top again. You might get faster results IRC #ubuntu and have you looked at Gparted forum.
[http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/)

Sharky

Thank you vcery much for your help.   I found the gparted forum by googling just a few minutes before you posted this.

I have a thread going on over there where I am getting some expert help.   [I'll link it here, in case anyone else needs this info.](http://gparted-forum.surf4.info/viewtopic.php?pid=23192#p23192)

Thanks again,
Matt

---

