---
title: "My PC is having more blackouts than kids at a college party when running Lucid Lynx"
date: 2010-06-01
forum: General Help
---

### Post by RaptorEmperor on 2010-06-01
I installed Lucid Lynx 10.04 LTS on a spare hard drive, and it's been acting buggy.

After installation, I installed any remaining updates.  I also installed the proprietary ATI driver recommended by Ubuntu.  The proprietary driver caused Ubuntu to get very laggy and slow, so I removed it and went back to the more responsive default driver that originally came with Ubuntu.  

More importantly, when I try to run Mozilla Firefox, the screen goes black, and I can't get any signal.  The monitor light goes yellow and says "No Signal", but I know the computer is still running because when the screen blacks out as I watch video I can still hear the sound playing.  I tried doing the three-finger salute in Ubuntu (ctrl+alt+delete) but it didn't work, I tried hitting random buttons and mashing the keyboard like a two-year old but nothing brought the screen back.

I had a similar experience when trying to test software with Wine.  When I tried to up the screen resolution to match my monitor's, the screen went black and the computer became unresponsive, just like with Firefox.

I've reinstalled Lucid Lynx three times over the course of 24 hours to no avail.  The bug still persists.  I'm typing this forum post in Windows 7 because Ubuntu is being a meanie and won't let me.

Stats for my computer are:
Hard drive:  Maxtor 20 gigabyte
CPU:  AMD Athlon 64 X2 
Motherboard:  VIA K8M800 (VT8380)
Video Card:  ATI Radeon HD 2600 Pro AGP w/512 megabytes of video RAM
RAM:  3072 megabytes DDR2
OS:  Ubuntu 10.04 Lucid Lynx LTS

I detached the Windows hard drives from the motherboards when testing Ubuntu because I wanted to test Ubuntu before overwriting Windows Boot Manager in the boot sector with GNU GRUB.  So they have no say in the matter.  

I believe the version of Firefox was 3.6.4.  Not sure, though.  Whichever version of Firefox ships with Lucid Lynx is what it was running.

I have some experience testing software from working with ReactOS, but I'm not very familiar with Linux, so I can't give any good guesses as to what's happening.  Maybe Ubuntu's blacking out when faced with a heavy CPU load, since Flash in Firefox and the games I was running in Wine were both memory-intensive.  I don't know.  

I have kept up with Ubuntu for the past five years or so, and it was my favorite Linux distro.  I was hoping to test it to see if it was feasible to triple-boot with my Windows XP and Windows 7, but I can't even test it to find out.  Sad to see Ubuntu's become so unstable.

Are there any solutions to this?  Has this bug already been reported?

---

### Post by RaptorEmperor on 2010-06-09
I forgot to mention, my sound card is an integrated "Realtek AC '97 Audio for VIA".

Tried installing Fedora Linux; had the same issue with the screen blacking out, though.  Sound gets glitchy after freezing, too, though not always.  Just as before, only way to fix the situation is a hard reboot, and then it'll just black out again shortly after I log back in. Starting to wonder if there's some shared component that's blowing up, maybe GNOME or something.  Anyone having any similar issues?  Has anyone even looked at this thread?

---

### Post by jwbrase on 2010-06-09
When the screen blacks out, does CTRL-ALT-F1 (or F2, F3, etc.) do anything?

Also, try opening up a terminal window and typing

```
dontzap --disable
```

This allows you to use a keyboard shortcut that is blocked by default in Ubuntu that restarts the X-Server. After doing this, and then doing something that blacks out the screen, does CTRL-ALT-Backspace do anything?

If not, holding down Alt + Sysreq and typing R, E, I, S, U, B (with a few seconds' pause between each letter) should reboot, and should be safer than a hard reset.

Other than that, have you tried using LXDE instead of GNOME with the proprietary driver? Our desktop back home has an ATI card, and started lagging under GNOME when I upgraded it to Jaunty, but runs fine under LXDE. I never tried rolling back to the default driver, though, so I can't confirm the blackout bug on that machine (and I'm currently on the other side of the Atlantic, so I can't test it). (I did, though, sometimes have trouble with hanging at a black screen on login with just a mouse pointer).

---

