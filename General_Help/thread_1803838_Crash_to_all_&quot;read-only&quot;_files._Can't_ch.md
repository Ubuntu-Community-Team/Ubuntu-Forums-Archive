---
title: "Crash to all &quot;read-only&quot; files. Can't change!!"
date: 2011-07-13
forum: General Help
---

### Post by Dscottmc7 on 2011-07-13
I've spent several days researching this...so if it is a duplicate I'd sure like to know (thanks)! 

_ I've crashed and am locked out_..***can't chmod,chown,or any other device to change Permissions. *** 

I THINK THIS PROBLEM IS UNIQUE as I think I screwed up! 

Crash:  Wanted to mount BOTH CDrom/dvds (each had different models, port numbers, etc).  Disk Utility sees them...but no deal.

-Last week I downloaded a program that included "dpkg," and I didn't realize it was in it...I think that is the problem...conflict w/ apt-get...dunno.

-Best answer (to mount 2 CDROMs) I got was "Insert a blank CD in each drive and reboot."  Seemed logical.  I did...CRASH!

Now it's a brick wall!  I can't change permissions because "read-only." (Cannot be opened or parsed...umask=0022, not using locking for read-only lock file), etc.

If it helps it's the HP n7674n IntelDuoCore -64, Nvidia GeForce 7300le, 4Gb RAM, 2-200Gb.HDDs.
Thank you in advance!!!  (really)
Scott

---

### Post by ikick on 2011-07-14
Hi mate,

Have you performed a fsck? That may come across some abnormalities within the filesystem.

Let me know how that goes.

---

### Post by Dscottmc7 on 2011-07-14
Ikik -- Many thanks, man!  Yea, I used about every command known to Linux/mankind...nada.

The problem still wasn't solved, so in utter desperation I saved all my files with "Live CD" and reinstalled.  (Forgot my Thunderbird files!...again!)

If anyone comes up with thoughts, I'll be checking back fairly often.  Thank you. [the remaining conundra are]:

-dpkg conflicts with apt...should never have accepted it, (dpkg, that is).
-Can get "Disk Utility" to see both (2) CDROM/DVDs, but can't mount BOTH.  (I wanted to save time in loading and unloading discs...and wasted a week cleaning up!)

I won't mark this SOLVED as the issues still face my other computer...IF I were to do the same.  So I'll watch the posts and pass the word.

Outstanding group of people.  I'm a newbie...only been with Ubuntu exclusively for 6+ years now! (duh...)
Thanko mucho
Scott

---

### Post by bsgjn on 2011-10-17
I have the same problem on a HP r810. No matter how I login as root, get:
Unable to write to /var/cache/apt, Not using locking for a read only file  /var/lib/dbkg/lock

I have re-installed Ubuntu 11.4 3 times, same problem
Anyone with a solution

---

