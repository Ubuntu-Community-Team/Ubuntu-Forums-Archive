---
title: "Slow booting of BIOS when booting Ubuntu"
date: 2010-01-18
forum: General Help
---

### Post by Nickemans on 2010-01-18
Well, I've been searching the forums for any posts that cover my problem, but most of the booting problems I've found are different from mine.

Anywho, the situation: Dell laptop, 2 partitions, first is Windows XP, second is Ubuntu Karmic.

Whenever I turn on my computer the first loading screen that shows up (is this the BIOS? Excuse my little knowledge of this stuff), before GRUB loads, is really slow. It takes about a minute to load.
However, whenever I restart from my XP partition, it suddenly loads fast! And this does not happen when restarting from my Ubuntu partition or anything.

Sooo. I'm kind of lost! Any of you have any suggestions?

Thanks!

---

### Post by Ahriman on 2010-01-18
When you first turn on your machine, the BIOS checks your RAM for any major errors. Depending on the amount of RAM you have (and if you have Quick Boot turned on in the BIOS options), this can take awhile.
When you restart, it skips this check; assuming that the RAM is ok. It doesn't matter what operating system you will use once the BIOS finishes.

---

### Post by Nickemans on 2010-01-18
It doesn't happen when restarting from Ubuntu though?
And also, back when I only had Windows on this same computer (I've had Vista and XP on here) and it always loaded fast, even when it was not restarting...

But what is that Quick Boot option?

---

### Post by Ahriman on 2010-01-18
The Quick Boot option differs depending on the brand of BIOS you have, but it's generally in the 'General Options' or 'Advanced Options' section of the BIOS.
You should be able to see what's happening behind the BIOS logo by hitting ESC while that logo is showing (you can also turn the logo off int he BIOS, too). That way you can see where it's stalling.

---

### Post by Nickemans on 2010-01-18
Oh right, I might have a look at that next time I boot my computer.
Is it easy to see where it's stalling?

---

### Post by Nickemans on 2010-01-18
I've had a look, but can't find the quick boot option..
Also, I just realised that the motherboard has been replaced a while back, and I think that's when the slow booting/loading started... Could that be it?

---

### Post by Ahriman on 2010-01-19
That could definately be the issue. When the BIOS is loading, it doesn't care about what operating system is on any of the storage devices at that time; it doesn't even care if there are ANY operating systems. All it's doing is checking what hardware devices are connected, if they respond properly, etc.
Different motherboards have different BIOSs, so this one may be set to non-optimum settings and causing this issue. Have a look through your manual to see what it recommends (generally 'Optimised Defaults' are the way to go, but this differs from BIOS to BIOS).

---

### Post by Nickemans on 2010-01-23
I found the quick boot option after all, so it boots super fast now!
Thanks =)

---

