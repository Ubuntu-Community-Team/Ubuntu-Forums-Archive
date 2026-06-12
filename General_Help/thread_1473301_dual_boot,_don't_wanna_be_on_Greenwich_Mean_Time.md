---
title: "dual boot, don't wanna be on Greenwich Mean Time"
date: 2010-05-05
forum: General Help
---

### Post by Tom_ZeCat on 2010-05-05
I have a dual boot machine with Ubuntu 8.04 and Windows XP Professional with each OS on a separate physical hard drive, as per the instructions in the thread, ***[Dual Boot, Two Hard Drives.]("http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot")***  It runs perfectly, except for one weird quirk.  

I'm in Omaha, NE and therefore have both OSes set to Central North American time.  If I'm in XP and then boot to Ubuntu and back into XP, my time jumps ahead 5 hours.  When I look in XP's control panel, it still says it's set on Central North American Time, but the time is incorrect.  It's five hours fast.  

At first I thought it was because XP was originally incorrectly set to Egyptian time and maybe XP thought I was still in that time zone, despite it being set to Central.  However, I looked up Egypt's time zone, and it's 8 hours ahead of me, not five.  I did an experiment.  I set my time zone to Mountain, which is one hour behind Central.  In this case, the time kept jumping ahead 6 hours instead of five.  Turns out, 5 hours ahead of Central and 6 hours ahead of Mountain is Greenwich Mean Time.  

I checked to see if my bios was perhaps set to Greenwich.  It wasn't.  It was set on Central after XP was in Central.  So I made sure the time was correctly on Central in XP and rebooted into Ubuntu.  In Ubuntu the time was still correct.  Then I rebooted, but before I allowed the computer to pull up XP, I went into the BIOS.  In the BIOS, the time was already incorrectly five hours ahead.  So somehow between booting from Ubuntu to XP, the PC's bios is being tricked into changing to Greenwich time before XP even comes up.  

WTF?  I'm not sure if it means anything, but my dual boot menu actually offers multiple choices of Ubuntu, even though I only installed it once.  Here's what I see:  

[IMG]http://tommeinenphotography.com/boot/bootup.jpg[/IMG]

If anyone knows how I can solve this problem without moving to England, I'd really appreciate a heads up.  Thanks.

---

### Post by Tom_ZeCat on 2010-05-05
An update: When I'm in Ubuntu and the time is correct and I reboot and go into Ubuntu again, the time remains correct.

---

### Post by john newbuntu on 2010-05-05
Still on Hardy? The following article might help you [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) especially the section "Multiple Boot Systems Time Conflicts". It talks about setting UTC=no in /etc/default/rcS.

---

