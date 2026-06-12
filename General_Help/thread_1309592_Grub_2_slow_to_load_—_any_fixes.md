---
title: "Grub 2 slow to load — any fixes?"
date: 2009-11-01
forum: General Help
---

### Post by Losgann Mor on 2009-11-01
Hi everyone,

Forgive me if others have posted with this same issue, but I did do several searches before posting and didn't see any other threads with the same problem that I'm having.

I did a fresh install of 9.10, and when I boot up or restart, it takes a (relatively) long time for GRUB 2 to load and display the grub menu. GRUB 1 only took about 5 or 6 seconds to load, but GRUB 2 is taking more than twice that, closer to 15. So any increase in boot speed (as in GRUB to desktop) is negated for me by how much longer it takes to get to GRUB in the first place. Maybe I've just been spoiled by 9.04, where there was a significant decrease in boot time compared to 8.10; the total boot time (e.g. power up or restart, through GRUB, to desktop) in 9.10 has definitely increased and makes me feel like I'm taking a step back towards 8.10. 

Once I'm actually in my 9.10 desktop, I'm happy, mind. Everyting (wireless, sound, etc.) has been working OTOB for me so far. And there are definitely some nice additions to the repos too, so overall I'm happy with Karmic. I realize my issue is really just an inconvenience which, in the overall pile of issues that other people are having with 9.10, is rather minor. But still, if anyone knows of any way to fix GRUB 2 so that it loads up closer to how GRUB 1 did, I'd be very grateful. Googling has turned me up nothing so far.

I don't know if this is a factor, but just in case it might be, I should mention that I'm dual booting with two hard drives, Windows (and the MBR) on one, and Ubuntu on the other. Also, I did a fresh install of Xubuntu 9.10 first, and then of Ubuntu 9.10 second, just to see if the issue was edition-specific, but it wasn't, I had the same slow GRUB 2 problem on both, so I'm assuming it's a GRUB 2 thing.

Thanks to anyone who can help.

---

### Post by Falcorian on 2009-11-01
> **tmleigh said:**
> I should mention that I'm dual booting with two hard drives, Windows (and the MBR) on one, and Ubuntu on the other.

I've heard there is a bug such that if they are on separate hard drives (or partitions even?) that it drastically slows down, but I haven't located the bug in launchpad yet (mainly do to not looking very hard).

I have MBR on separate drives, and it takes ~20 seconds for GRUB2 to load (that is, from the point where my BIOS starts loading it to the point where the list of OSes pops up). I have no solution for you, I'm looking for one myself. :(

---

### Post by Falcorian on 2009-11-01
I think this is the bug in question: [Bug #420933]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933")

---

### Post by hal8000 on 2009-11-01
I posted this sometime earlier:

[http://ubuntuforums.org/showthread.php?t=1309398](http://ubuntuforums.org/showthread.php?t=1309398)


Grub 2 is the culprit, I also have 2 hard drives, I just booted into hardy, edited
menu.lst on Hardy and installed grub 1 to coontrol booting. This saved the30 or 40 seconds
of grub 2 to load, although karmic is a lot longer at loading than Hardy was.

Once at the desktop, I have not found any other problem yet and will use sysv-rv-conf to
streamline my boot time

Hope that helps.

---

