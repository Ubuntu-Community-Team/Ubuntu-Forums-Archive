---
title: "Is my processor working too hard"
date: 2009-11-04
forum: General Help
---

### Post by rmccutchan on 2009-11-04
I am new to linux, so I am not real familiar with the command prompt, but know how to get there and enter commands.

It seems that this computer has slowed down quite quite a bit lately.  I installed Ubuntu approximately 2 months ago.

I have a Dell Optiplex 280 with a Pentium 4  2.8 gHz processor and 2 gigs of ram, 80 gig hd that is only less than 1/2 full.

I am a digital photographer and use Rawtherapee and Gimp to process photographs.   When I have Rawtherapee convert a bunch of files to PNG, the processor goes to 100% and stays there for a long time.  10 or 15 minutes or so for 60-70 pictures, and everything turns a medium gray while it is doing so.  Also, when I am editing in Gimp, the processor peaks at 100% very frequently, and all brush actions are very slow and choppy.  It seems to get worse as time goes on.  Also, everything in general seems to be a little slower than it was a month ago, and the processor hits 100% more often.

When I let the computer sit idle for a few minutes with no applications running, the processor runs at about 8-10% +-.  As I am typing this, the processor is bouncing around at about 20%, with an occasional spike to 50%.   I have wobbly windows and rotating desktops turned on, if that matters.

Does this sound normal for this processor and the amount of work I am asking it to do?  Also, would a good graphics card be benificial?  I just have whatever came stock on the motherboard.  Or, do I just need more horsepower (dual or quad core processor)?

Thank you in advance.

Bob

---

### Post by IllegalCharacter on 2009-11-04
Go to System -> Administration -> System Monitor

Click the Processes tab, and click % CPU to sort the processes by CPU time.

If you watch that for a little while, it should tell you what process(es) are using up your CPU time.

---

### Post by rmccutchan on 2009-11-04
Everything is at zero % except:

compiz.real.......1%
firefox..............1-3%
gnome system monitor.........6-8%
xorg...........1-8%

If I think I understand, this isn't much, and I could use more horsepower.  Correct?

---

