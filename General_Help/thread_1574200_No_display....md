---
title: "No display..."
date: 2010-09-13
forum: General Help
---

### Post by ian2112 on 2010-09-13
Hi All,

I have no clue where to start with this issue... any ideas would be helpful.  Here's the scoop:

I've been running fine (9 months) with my new LG LDC monitor.  Two weeks ago I decided to also connect my old ViewSonic monitor.  Ever since unplugging the ViewSonic, the LG Monitor stays black after going past the Grub menu where I select Ubuntu.  The only way I can get it to display the Ubuntu login screen is to physically unplug the monitor and plug it back in.  Maybe something in the boot up process is not sensing the display?  Or perhaps first waiting for the now disconnected ViewSonic???

Any ideas???

---

### Post by anglican on 2010-09-14
> **ian2112 said:**
> Hi All,

I have no clue where to start with this issue... any ideas would be helpful.  Here's the scoop:

I've been running fine (9 months) with my new LG LDC monitor.  Two weeks ago I decided to also connect my old ViewSonic monitor.  Ever since unplugging the ViewSonic, the LG Monitor stays black after going past the Grub menu where I select Ubuntu.  The only way I can get it to display the Ubuntu login screen is to physically unplug the monitor and plug it back in.  Maybe something in the boot up process is not sensing the display?  Or perhaps first waiting for the now disconnected ViewSonic???

Any ideas???Try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```with the LG monitor plugged in.

H

---

### Post by ian2112 on 2010-09-14
Hi

I gave the command a try.  The command was accepted error free, but didn't resolve my problem.  I tried restarting my desktop I still need to disconnect and re-connect the monitor cable.

A couple other questions / thoughts...

- Are there any commands I can issue that could tell me more information about the communications between my desktop and the monitor ("System / Preferences / Display" isn't all that helpful)?

- The command that I tried... can I eliminate anything (potentially) as the source of the problem?

- Any other thoughts or ideas?

As always, I appreciate the guidance...

Thx,
Ian

---

### Post by anglican on 2010-09-15
> **ian2112 said:**
> Hi
A couple other questions / thoughts...

- Are there any commands I can issue that could tell me more information about the communications between my desktop and the monitor ("System / Preferences / Display" isn't all that helpful)?

- The command that I tried... can I eliminate anything (potentially) as the source of the problem?

- Any other thoughts or ideas?

As always, I appreciate the guidance...

Thx,
IanYou could try:
```
sudo ddcprobe
or
sudo hwinfo --monitor
```(which assume you've installed the xresprobe and hwinfo packages). Otherwise, have you got an /etc/X11/xorg.conf file that's causing problems?

H

---

### Post by ian2112 on 2010-09-16
Here's the contents of ddcprobe.  Nothing seems out of place, but I also don't fully appreciate what I'm looking at...

Also - tonight I tried booting into Windows Vista and it worked no problem, so I know the issue isn't with the hardware itself.  For some reason... Ubuntu isn't correctly detecting the monitor. 


vbe: VESA 3.0 detected.
oem: ATI ATOMBIOS
vendor: (C) 1988-2005, ATI Technologies Inc.
product: RV670 01.00
memory: 16384kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 1280x1024x256
mode: 640x480x64k
mode: 800x600x64k
mode: 1024x768x64k
mode: 1280x1024x64k
mode: 320x200x64k
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid: 
edid: 1 3
id: 56ff
eisa: GSM56ff
serial: 0002b99f
manufacture: 7 2009
input: separate sync, sync on green, analog signal.
screensize: 48 27
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
ctiming: 1680x1680@60
ctiming: 1280x1024@75
ctiming: 1280x1024@60
ctiming: 1152x864@75
dtiming: 1920x1080@59
dtiming: 1920x1080@67
monitorrange: 30-83, 56-75
monitorname: W2243

---

### Post by ian2112 on 2010-09-17
I upgraded from 9.10 to 10.04 and this seems to have resolved my issue.  It would have been nice to understand the cause and fix... but better than nothing!!!

Thanks for the help,
Ian

---

