---
title: "System freezes, no apparent cause"
date: 2012-03-14
forum: General Help
---

### Post by whitesuit on 2012-03-14
Hi, I'm running Ubuntu 11.10:

Linux desktop 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux

I'm experiencing random system freezes, where if I have some sound running it keeps looping.

I ran memtest for 1h+, more than 5 tests and no errors show up. I checked cpu and gpu (nvidia geforce 9400 gt, using current nvidia drivers from ubuntu) temperatures, none are overheating. I reinstalled the system (ext4 partition), in case my partition was screwed up, but no help.

It seems random. For instance, I'm browsing a website and then suddenly everything stops. If there is some music playing, then the last few seconds keep repeating.

I checked almost every log in /var/log but nothing suspicious shows up also.

Any idea how to proceed?

Thanks!

---

### Post by colorfultrixe on 2012-03-14
Hi Hun sorry for hijacking your thread I,m having issues too with freezing 3 times today, I was using firefox and playing a CD,  I had to reboot, Also done same run the memtest and my lappy passed 
Trixe

---

### Post by colorfultrixe on 2012-03-14
Hi Hun sorry for hijacking your thread I,m having issues too with freezing 3 times today, I was using firefox and playing a CD,  I had to reboot, Also done same run the memtest and my lappy passed 
Trixe

---

### Post by 2F4U on 2012-03-14
You should run at least one complete cycle of memtest. The test are all different and therefore are testing different problem areas. Just because 5 single tests succeed does not mean that the others are also successful.
I once had a RAM chip that had errors only in the second run, but that at least was consistent.

---

### Post by Hylas de Niall on 2012-03-14
This is quite common, it would seem.

I had the same problem with 11.10 through various installs from various different sources (different iso's and magazine disks).

In the end i reverted to 10.10 on my desktop, and that's been rock-solid. I *think* the problems might be down to the newer kernels or Gnome 3.

I wish i could offer advice, but no advice offered to me on this forum showed any hardware or software errors in my case.

---

### Post by whitesuit on 2012-03-14
> **2F4U said:**
> You should run at least one complete cycle of memtest. The test are all different and therefore are testing different problem areas. Just because 5 single tests succeed does not mean that the others are also successful.
I once had a RAM chip that had errors only in the second run, but that at least was consistent.

I didn't know there was a "cycle". When I run it shows a screen like this: 

[IMG]http://www.memtest.org/pics/i875-big.gif[/IMG]

When I ran it, I got 5 Pass. I thought these were 5 "cycles".
How can I know it completed a full "cycle"?

I had those freezes some time ago, which were caused by a faulty memory stick. After I exchanged it, the problems stopped. Now they're back. I think the most likely case is that one of the sticks is faulty again. 

I took one of them out and am gonna see if any other freezes crop up.

---

