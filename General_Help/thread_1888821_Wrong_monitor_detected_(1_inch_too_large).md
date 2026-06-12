---
title: "Wrong monitor detected (1 inch too large)"
date: 2011-11-30
forum: General Help
---

### Post by porchrat on 2011-11-30
Hi all

This is hardly a crippling problem but it is annoying.

I'm running Ubuntu 10.04 64 bit but it keeps autodetecting the wrong size monitor. Ubuntu thinks I'm running a 23 inch monitor when it is actually a 22inch. Can I force the system to run as though it were using a 22 inch monitor?

I'm running the fglrx from the repositories but I could never get the catalyst control centre to run as it kept telling me it didn't have an ATI driver installed. Which is weird.

---

### Post by ObsidianCommand on 2011-11-30
Try removing the fglrx driver and install the ati catalyst driver from the amd site, it may be in relation to the fglrx driver.

---

### Post by mcduck on 2011-11-30
It shouldn't make any difference what the physical dimensions of your monitor are, the only meaningful values are resolution and refresh rate.

If you can tell more details about what kind of problems you are having with the monitor, then perhaps we'll be able to help you to solve them. If it's just that some program displays wrong infomation about the display, then I recommend you just ingore it.

---

### Post by efflandt on 2011-11-30
You have not said why size matters. X used to think that my 32" 1080p HDTV was 51", but that was a non-issue as long as it outputs 1920x1080 @ ~60 Hz. /var/log/Xorg.0.log in 11.10 no longer lists a size and I have not figured out what size it uses to calculate 42 dpi.

If your problem is overscan, does the menu on your monitor have any setting to adjust to the video signal either auto or manually adjustable horiz, vertical, position, etc.?

Even though default settings for nvidia driver would tend to overscan if I set my HDTV to 1920x1080, my TV has a mode called "Just Scan" that automatically sizes whatever signal it is receiving to perfectly fill the screen. So I do not need to adjust the overscan slider in NVIDIA X Server Settings. I am currently using DVI to HDMI cable. If using VGA there is less of a chance of Linux knowing optimum resolution and sizing.

---

### Post by porchrat on 2011-12-01
Sorry the real problem is that the entire screen is horizontally too far to the left. So I can never see the first character of each line in the terminal. Obviously I can just shrink the terminal window (or whatever window I'm using) to fit the screen but that is annoying.

I tried removing the fglrx driver that hasn't fixed it.

I had assumed the screwed up screen alignment was a result of the machine thinking the monitor was larger than it actually was. I realise now how stupid that was because as you guys pointed out all that matters is resolution (and refresh rate but that isn't related to my problem).

Normally I would just solve this mess by using the alignment controls on the screen but they are locked for some unknown reason.

---

