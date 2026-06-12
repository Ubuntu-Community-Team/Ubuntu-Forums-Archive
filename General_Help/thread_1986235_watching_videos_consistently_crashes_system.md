---
title: "watching videos consistently crashes system"
date: 2012-05-24
forum: General Help
---

### Post by ronwell on 2012-05-24
Hi!  So I'm running Ubuntu 12.04 on my fairly old and beat up Thinkpad T60p.  For the most part everything runs smoothly.  But for some reason, watching videos almost always causes Ubuntu to crash and my computer to shut down.

I've been having this problem for a while.  I'm pretty sure it's not a hardware thing, because it was never an issue with 11.04.  When I installed 11.10, it started happening with downloaded video files that I was playing back. Now with 12.04 it's started happening with streaming as well.  Basically I can't watch any videos without crashing the system.

I don't know how to diagnose or fix this problem.  The crash happens so fast that I can't read the text that briefly pops up on the screen before shutdown.  I think I've seen "could not write bytes: broken pipe" a couple times.  Is there a crash log somewhere that I could maybe at least find out what's happening?  Should I just bite the bullet and downgrade all the way back to 11.04?  Any help would be greatly appreciated.  I miss being able to watch TV shows :(

---

### Post by ronwell on 2012-05-25
Bump?

I know it's a pretty vague problem, but it's definitely real.  If anyone knows, at the least, a way that I could diagnose what's actually happening when the system crashes, that would be so awesome. 

Everything is always perfectly stable except when I start playing back or streaming a video.  It usually happens at a random, unpredictable time during the course of the video, not right as I hit play.

---

### Post by 2F4U on 2012-05-25
Did you look into the system log files? That would be the first thing I would do after a crash. Next thing would be to monitor temperatures during normal operation and when watching video. If you had such problems with other versions, it could be worth verifying that your RAM is working fine by running memtest, either from the existing installation (should be in the grub menu) or from a liveCD.

---

### Post by sudodus on 2012-05-25
I think that your problem is because the newer Ubuntu systems need more powerful cpu and or graphics processors.
 
This can cause various problems, often choppy or lagging playing. But I guess that with some settings, a bug might be activated causing a crash.

I'm also using old hardware and now I run a desktop environment with lighter foot-print. Lubuntu 12.04 LTS makes my video experience even better than Ubuntu 10.04 LTS. Have a look at this thread
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1986777_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1986777")

If a lighter DE doesn't solve your problem, you have to look for the cause somewhere else: bad RAM or some other bad hardware, or some bad software (maybe a corrupt file).

You can test your RAM with memtest at the grub menu. Run it for hours (overnight). There should be *no* error at all.

If you can play video running Lubuntu 12.04 booted from a CD or USB drive, it should be possible to get a working system by installing from that CD.

---

### Post by philinux on 2012-05-25
> **ronwell said:**
> Bump?

I know it's a pretty vague problem, but it's definitely real.  If anyone knows, at the least, a way that I could diagnose what's actually happening when the system crashes, that would be so awesome. 

Everything is always perfectly stable except when I start playing back or streaming a video.  It usually happens at a random, unpredictable time during the course of the video, not right as I hit play.

Right click the vid and uncheck "enable hardware acceleration".

See if thats it.

---

### Post by ronwell on 2012-05-25
Thank you for all the tips!  Disabling hardware acceleration in VLC does seem to have stopped it happening in that context, which is great.   Is there any way to also prevent Firefox (or Chrome) from doing hardware acceleration with streaming video? Or would that be up to the individual streaming service?

Running memtest sounds like a good idea, for sure, but I don't quite get how to access it.  I looked up "grub," and I've gathered that accessing this menu is supposed to be an option at start-up (is that right?).  But when I boot, my system goes straight into Ubuntu, it never stops to ask.

edit: Found and unchecked the hardware acceleration option in Firefox.  Hopefully that'll do it. But if someone has a minute to help me understand how grub/memtest works I would really appreciate it!

---

### Post by sudodus on 2012-05-25
Try to press the shift key at boot. If that does not work see
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1939408_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1939408")

---

