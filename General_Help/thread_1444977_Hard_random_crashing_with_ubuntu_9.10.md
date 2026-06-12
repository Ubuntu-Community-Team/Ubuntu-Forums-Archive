---
title: "Hard random crashing with ubuntu 9.10"
date: 2010-04-02
forum: General Help
---

### Post by jzambon on 2010-04-02
Hey all,

I've been experiencing some hard random crashing with Ubuntu 9.10.  When I say hard, I mean REISUB can't even bring it back and shells on another machine are unresponsive.  Completely unresponsive to mouse or keyboard input - cursor just sits on the screen, frozen.

This tends to happen when I'm running PS3 Media Server, encoding and streaming video.  However, it has also happened with relatively light tasks (torrents) or when its just sitting still for a while.

My instincts suggest a Memtest might find some corrupt memory and this may be a hardware issue.  I'm currently running that.  Previous trials have turned up no issues, though.  I am not overclocking or anything of that sort.  I have experienced crashing problems with the video card (ATI) in the past but the proprietary driver (provided by Envy) seems to do a lot better now.

If anyone has any ideas about some other stress-testing I could throw at it, or what I could do to try to isolate the problem, it would be greatly appreciated.

It has been completely updated through 9.10, if you have any suggestions or what you would need for more info, please let me know.

Thanks!

-Joe

---

### Post by lovecats on 2010-04-02
I came across the same problem. IT just happened when I installed Ubantu.
After days of research, I finally resolve it.
it's because of my config of the hard drive.the default config is SATA and something else. I changed it into the ordinary mode. And the problem never happens.

> **jzambon said:**
> Hey all,

I've been experiencing some hard random crashing with Ubuntu 9.10.  When I say hard, I mean REISUB can't even bring it back and shells on another machine are unresponsive.  Completely unresponsive to mouse or keyboard input - cursor just sits on the screen, frozen.

This tends to happen when I'm running PS3 Media Server, encoding and streaming video.  However, it has also happened with relatively light tasks (torrents) or when its just sitting still for a while.

My instincts suggest a Memtest might find some corrupt memory and this may be a hardware issue.  I'm currently running that.  Previous trials have turned up no issues, though.  I am not overclocking or anything of that sort.  I have experienced crashing problems with the video card (ATI) in the past but the proprietary driver (provided by Envy) seems to do a lot better now.

If anyone has any ideas about some other stress-testing I could throw at it, or what I could do [r4i gold]("http://r4-dsi.be") to try to isolate the problem, it would be greatly appreciated.

It has been completely updated through 9.10, if you have any suggestions or what you would need for more info, please let me know.

Thanks!

-Joe

---

### Post by jzambon on 2010-04-02
> it's because of my config of the hard drive.the default config is SATA and something else. I changed it into the ordinary mode.

I'm a little confused by your suggestion. Is this something that you do when setting up Ubuntu?  I'd like to hold off on reinstallation until most possibilities have been exhausted.

Memtest has been running 8.5+ hours (65%) and still has not uncovered any errors.  Any suggestions for other possibilities?

Thanks.

---

### Post by shebaw on 2010-04-02
It may be driver problems, I had similar problems with my driver for graphics card(ATi driver) and my driver for my wireless card conflicting.

---

### Post by jzambon on 2010-04-02
Any tips on how to check for driver conflicts?  I haven't installed my wireless driver because I use wired internet and wanted to limit the amount of hardware on this machine.

Thanks!

---

### Post by electricguy on 2010-04-06
Could anyone there able to suggest or recommend action items items to resolve this problem. of hard random crashing.

I have same problem and don't know how to fix it. I am new to linux and just installed yesterday Ubuntu 9.10.

My system consists of the the following hardware:

DG41TY Intel motherboard
Intel Core 2 Dou Procesor
SATA HDD
SATA Samsung SH-S223 DVD drive

Any support would be highly appreciated

---

### Post by jzambon on 2010-04-12
electricguy, sorry to hear of your problems...although misery does love company :-P

Here is what I have tried so far...
*memtest*
I ran this for 36 hours, and it came up with no faults on my 2x1GB sticks.
See: [http://ubuntuforums.org/showthread.php?t=874682](http://ubuntuforums.org/showthread.php?t=874682)
*System*
I have been experiencing crashes on both Ubuntu 9.10 and Kubuntu 9.10, I've recently gone with an install of the latter due to my personal preference of KDE over Gnome.
*Graphics Card/Drivers*
I recently purchased a new ATI video card to replace my old one.  I am using the proprietary drivers.
See: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
*CPU*
I've stress-tested the CPU (Phoronix Test Suite, stresscpu2) and noticed that it was reaching dangerously high temperatures.  I've tinkered with the fan control settings and I believe have gotten that situation under control...
See: [http://ubuntuforums.org/showthread.php?t=1297008](http://ubuntuforums.org/showthread.php?t=1297008)
I also had a problem with the sensors having conflicts and was unable to get any temps/RPMS.  I did the GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax" hack and that seems to work, although I have been warned it may make the system unstable.
See: [http://ubuntuforums.org/showthread.php?t=1321293](http://ubuntuforums.org/showthread.php?t=1321293)

Currently its been running with a CPU load test with no issues for 1 1/2 hours.  Keep in mind that I haven't overclocked, everything is 100% stock.

The crashing seems to happen completely out of the blue.  I was typing a paper in OpenOffice last weekend (saving often), and it crashed.  I was watching a movie on my PS3 via PS3 Media Server ([https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)) and it crashed.  Keep in mind that this is a hard crash (no mouse/keyboard input, not able to REISUB) with no rhyme/reason to it.  Sometimes it may crash just while idling...

If CPU overheating is the culprit and the system remains up for a day or so, I'll post and let you know.  I'm not thinking this is likely as it has crashed during idling and the heat sink on top of the CPU is huge (Rosewill powered heatsink).

I'm *really* open to any other suggestions!

Thanks for the help!

---

### Post by jzambon on 2010-04-12
Checked in repeatedly while at work.  A top showed that the CPU stress test was going.  Then sometime late in the afternoon (approx. 3 hours into the test) it died and the SSH connection dropped out.

Restarted when I got home, current uptime is 1hour 15min.

Again, any suggestions are very much welcome, thanks!

---

### Post by jzambon on 2010-04-14
I'm beginning to think this may be a power supply issue.  1) its easier to change out the Power Supply, rather than get new mobo/cpu/ram.  2) this is completely random and occurs without any warning 3) it occurs in XP and in Ubuntu.

Any other thoughts would be greatly appreciated.

---

