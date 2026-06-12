---
title: "Long System Beep During Shutdown"
date: 2009-10-30
forum: General Help
---

### Post by zzzBrett on 2009-10-30
After i shutdown kubuntu 9.10, the ~4-5 seconds before the machine powers off, i hear a loud system beep (continuous), then power turns off.  This is after the kubuntu 'unloading' bar is complete.

I have tried adding adding blacklist pcspkr to the end of /etc/modprobe.d/blacklist.conf, but that seems to have no effect.  Where is this beep coming from?

It seems to be similar to the problem found in the thread below, but I couldn't make out whether or not a solution was found:
[http://fixunix.com/suse/527913-beep-shutdown.html](http://fixunix.com/suse/527913-beep-shutdown.html)

---

### Post by zzzBrett on 2009-10-31
Suggestions?

---

### Post by dcs3jah on 2009-11-12
I've got the same problem. My beeps aren't always continuous though - maybe 4 beeps a seconds or so. I'm unsure as to whether it's a software or hardware issue (I've had a couple of hard freezes in the last month too). Sometime I shut down and it doesn't do it.
For reference, my motherboard is an "MSI P45 Zilent iP45 Socket 775".

I'm about to run a full memcheck and reinstall Ubuntu to see if it helps.

---

### Post by majia on 2009-11-12
I'm running ubuntu 9.10, and I confirm this problem as well. The PC speaker beeps randomly before the power is off, even my pc speaker has already been blacklisted. No such problem on jaunty. 

Another issue is that my lan led is still on after I shutdown the system, no such issue on jaunty and windows. 

Any suggestions?

Thank you all in advance!

---

### Post by Thunder Teaser on 2009-11-12
I can confirm this too on Karmic. Precisely, it started happening after upgrading the kernel to 2.6.31-15.**50**. The pcspkr workaround is not working. Has anyone reported this on Launchpad already?

---

### Post by zzzBrett on 2009-11-15
No, haven't reported yet.

---

### Post by gordong11 on 2009-11-21
I solved for me anyway.

I opened the Software center and downloaded/installed gnome alsa mixer.

Then there is a lever for beep, it was maxed so I just muted it....and now no more beep. 

Im not running a laptop tho.

---

### Post by zzzBrett on 2009-11-21
Thanks--i'll try that in about a week when i get back to the computer and post back.  Note: I believe you can also use alsamixer, the terminal-version of the volume controller.

---

### Post by gordong11 on 2009-11-21
yes you can use the terminal version...but trust me gnome is 110x better, and easier.

---

### Post by zzzBrett on 2009-12-07
My 'beep' volume is at zero -- not the problem.  Also, the beep sounds before halt, not in the presence of any gui.

Any other suggestions?

---

### Post by dimoftheyard on 2009-12-26
Does anybody have a solution? I've got the same problem. Not always, but often my laptops beeps tremendously loud during shutdown, directly before power off. The length varies as well, but it can be up to 5 seconds and more.
I'm running Kubuntu 9.10 with the latest upgrades. pcspkr is blacklisted in /etc/modprobe.d/blacklist.conf, and lsmod | grep pcspkr shows nothing. In the mixer PC Beep is at level 0 and muted. But I still here that sound.
I'd greatly appreciate any hint on how to get rid of this noise.

---

### Post by zzzBrett on 2010-01-03
bump

---

### Post by dimoftheyard on 2010-01-10
It looks like I have found a workaround. As I posted in [http://ubuntuforums.org/showthread.php?t=1367499](http://ubuntuforums.org/showthread.php?t=1367499) , turning of the splash screen seems to have fixed the problem for me. I don't have the slightest idea what the problem was (except that it only happend when the xserver was started), but if this turnes out to be a permanent solution I'm more than happy.

---

### Post by zzzBrett on 2010-01-10
> **dimoftheyard said:**
> It looks like I have found a workaround. As I posted in [http://ubuntuforums.org/showthread.php?t=1367499](http://ubuntuforums.org/showthread.php?t=1367499) , turning of the splash screen seems to have fixed the problem for me. I don't have the slightest idea what the problem was (except that it only happend when the xserver was started), but if this turnes out to be a permanent solution I'm more than happy.

I'll try this out - thanks!

---

### Post by kajman on 2010-01-23
Same problem here. I'll check out if turning off the splash screen will help. But very annoying thou. Why isn't this bug fixed yet?

---

### Post by kajman on 2010-01-23
On on the other thought how is it even possible if the pc speaker module is blacklistet thus not loaded? Who's generating the beep?! :confused:

---

### Post by zzzBrett on 2010-01-29
Changing the grub setting didn't help for me. This is an extremely annoying issue. Sometimes, now, it will just stay beeping until I manually hold the power button for ten seconds. Has anyone else experienced this issue? Any more suggestions?

---

