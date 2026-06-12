---
title: "Ubuntu vs. Win7 time issue"
date: 2009-10-20
forum: General Help
---

### Post by pvillestang on 2009-10-20
So I've had Ubuntu working on the computer just fine for 9 months. I partitioned the HDD and added a copy of Win7, and now there's a time issue:

When I boot, and check the BIOS time, it shows the time correct in relation to my current time zone. I boot to Ubuntu 9.10, and it's the same. Now I boot into Win7, and the time shows as 5 or 6 hours ahead (roughly GMT, if I'm not mistaken). Now if I adjust the Win7 time and have a server automatically sync it, it screws up my BIOS clock, and in turn screws up the GRUB loader, showing it the last time the drive was accessed was in the future. BIOS is on an ASUS M3A78-EM board (AMD).

My question here, is there a patch from either OS that would fix this issue?

Thanks

---

### Post by Giblet5 on 2009-10-20
My guess is: somewhere in Win7, you have turned on UTC system time.

That will sync the motherboard's RTC to UTC as well.

Turn that off and fix all the clocks.

Easy, huh?

Note: It's not GMT anymore - it's UTC, for Universal Time Constant, although I'm doubtful that anyone not from Earth is losing sleep trying to figure out how to comply with that standard. Maybe the Galactic Imperial Time Keepers work for Microsoft, now....

---

### Post by pvillestang on 2009-10-20
I have it set to Central Time (US and Canada) and set to sync with the time server (a-nist) and after the sync is correct, but after the sync is when the issues arise.

---

### Post by QIII on 2009-10-20
I haven't fiddled with this on my Karmic machines, and I don't have any desire to dual boot Win7, but it could be either OS.

I think (not at my Ubuntu machines right now) that Karmic still has

/etc/default/rcS 

Try to go there and set UTC=no.

Works on Vista and XP dual boots with Jaunty.


BTW:  UTC (don't ask me about the order of the letters in the acronym) is actually "Coordinated Universal Time".
GMT is still used (albeit with the understanding that the UTC atomic time is really "the time") as Zulu in many military settings.
The Universal Time Constant is a Physics concept.

---

### Post by bruno9779 on 2009-10-20
Try removing win7.

That will solve a lot of your problems. :lolflag:

It is clear that it is a Win7 issue; maybe the post should be moved to testimonials?

---

### Post by QIII on 2009-10-20
Don't think it is necessarily a Win7 issue.  The same occurs in XP and Vista dual boots.

And although it would be nice to say

```
sudo apt-get remove --purge windows*
```that is not really a very pragmatic course of action...

Alas.

I make an obscene amount of money with MS...  Just a harlot, I guess.

---

### Post by pvillestang on 2009-10-20
Well, I need to be on top of M$, since I do IT support and all my clients use M$.

---

### Post by Giblet5 on 2009-10-20
> **QIII said:**
> ```
sudo apt-get remove --purge windows*
```that is not really a very pragmatic course of action...


I tried that and it spits out an error: ```
rc = 0: balmer wept
```

Interesting.

---

### Post by Giblet5 on 2009-10-20
> **pvillestang said:**
> Well, I need to be on top of M$, since I do IT support and all my clients use M$.

Well, this HAS to be a setting on Win7.

You fix the BIOS clock. Everything is cool until you boot Win7, right?

This box boots Win7, Vista64, XP32, CentOS, Jaunty, Karmic, and RedHat EL and I don't have this problem at all.

Win7 isn't really released yet, right? Just sayin'...

---

### Post by pvillestang on 2009-10-20
It's a RC ultimate 64 bit architecture, I believe, although I can't be certain since I'm not at that comp right now, and I don't have Terminal services hooked up, so no remote access to that PC.

---

### Post by Mark Phelps on 2009-10-20
It's NOT strictly a Win7 issue.  Why? Because I'm running multiple OSs on my box, including Win7, and I do NOT have that problem at all.

It's a difference between default time settings used in the two OSs.  One has UTC enabled, the other does not.  So, each time you switch OSs, your RTC gets reset.  You need them both to have the same settings.

---

### Post by P4man on 2009-10-20
> **Giblet5 said:**
> Well, this HAS to be a setting on Win7.

You fix the BIOS clock. Everything is cool until you boot Win7, right?


Everything is also cool in windows 7 until you boot linux. Its just a different way of interpreting the system clock, no OS is really to blame. Its just thats easy to fix in only one of them.

And btw, If *you* dont have that problem, then its probably because your local time is utc time or you dont have daylight saving. Might change in a few weeks ;) Ive always had this issue with any combination of windows and linux.

---

### Post by pvillestang on 2009-10-24
> **QIII said:**
> I haven't fiddled with this on my Karmic machines, and I don't have any desire to dual boot Win7, but it could be either OS.

I think (not at my Ubuntu machines right now) that Karmic still has

/etc/default/rcS 

Try to go there and set UTC=no.

Works on Vista and XP dual boots with Jaunty.


BTW:  UTC (don't ask me about the order of the letters in the acronym) is actually "Coordinated Universal Time".
GMT is still used (albeit with the understanding that the UTC atomic time is really "the time") as Zulu in many military settings.
The Universal Time Constant is a Physics concept.

Fixed the issue, thanks!

---

