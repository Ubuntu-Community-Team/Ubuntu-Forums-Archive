---
title: "Radeon 9800 Pro issue"
date: 2009-11-16
forum: General Help
---

### Post by Mutant Corn on 2009-11-16
Tried searching this, but I wasn't sure what to put in.

I've just installed and updated xubuntu 8.04 on a junker I put together. 2.0Ghz Celeron, 440MB RAM. I'm getting artifacts on the screen, and it bogs down terribly on youtube videos. It *will* run at full resolution, however. (the desktop, not youtube)

If this helps:
I still get artifacts in the BIOS splash screen
It's a 128MB card, AGP slot
The motherboard is from an HP Pavilion, and has no onboard video
Nothing should be overheating...there are 3 chassis fans, plus the ones on the ATI, the CPU, and the power supply.

Everything else seems to be fine. The cpu is a *bit* sluggish but works fine, and I'm well within my RAM limits.

---

### Post by gordintoronto on 2009-11-16
If you get artifacts in the BIOS screen, there are hardware issues, nothing to do with Xubuntu.  What kind of screen does the computer have?

No surprise that it bogs down on Youtube, the processor is slow.  Did you install the proprietary video driver?

---

### Post by Mutant Corn on 2009-11-16
Yep, I've just noticed that the processor jumps to 100% when I hit play on youtube. Seems odd though...I've used youtube just fine with much slower systems than this. I did install the proprietary driver. The only noticeable change was that it jumped the desktop resolution up quite a bit.

So it's completely a hardware issue? How do I troubleshoot that? The only other card I have is an ancient GEForce2 MX...it's not even AGP.


edit: The screen is a Dell CRT that came with a Optiplex. Thre's nothing wrong with it AFAIK...works fine with my other computers.


edit: Thought I'd add this in...ignore this if it's too irrelevant. I originally had a 2.8GHz Pentium 4 in this machine, but I got no video while it was in. Same with a 2.8 gig Celeron, which is currently running fine in another computer. Also tried a 2.5 GHz pentium and it ran horribly slow. What's up with that?

---

### Post by gordintoronto on 2009-11-16
You understand that the Celeron processor is slower than a non-Celeron with the same clock speed?

If you decide to run the current version of Xbuntu, you will probably get better results with the GeForce2 card.  It might be worthwhile trying it, to see if the artifacts go away.  If you decide to change cards, remove the proprietary driver first.

Gee, I've never used Ubuntu with a CRT...

---

