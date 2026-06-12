---
title: "System-wide random pauses"
date: 2009-10-12
forum: General Help
---

### Post by highlycaffeinated on 2009-10-12
I'm new to Ubuntu (8+ years on Debian; not new to Linux) and recently installed Ubuntu 9.04 on an AMD dual core machine (previously ran Debian) in order to check out XBMC in an HTPC environment. Since install I have been having system-wide random "pauses" that recover automagically and without issue. It's as if you put the entire system on hold for a random period of time (usually 3-20 seconds). I've seen a number of threads that deal with system hangs, but this is not a hang (system recovers completely as if it didn't happen). Htop running during a pause sometimes goes high-cpu on one core briefly after recovery. Since nothing is logged I'm at a loss as to how to troubleshoot. I'm really bummed because everything is working SO well in Ubuntu except for this, and it's a dealbreaker in a HTPC scenario. I've tried upgrading to a newer kernel (2.6.30-generic) but same thing. I thought maybe the Forcedeth ethernet may be the culprit (on a gigabit switch) but dropping the rate to 100MBFull did nothing.

Any clue how I can go about narrowing down the problem? It happens no matter the system state or if X (gdm) is running.

Thoughts? Ideas? Thread-links?

Thanks!
-Highly

---

### Post by P4man on 2009-10-13
is dmesg giving any hints?

---

### Post by XP_convert on 2009-10-13
see if there are updates for the CPU / mobo / bios.  I had a problem with an Intel CPU that would hang up whenever I ran MS Outlook, it was a pain until I found out there was an Intel fix for it.  The problem was caused by Intel's poor manufacturing of the chip, causing it to loop.  Intel issued some type of firware update for Windows that fixed it.

---

### Post by Kevbert on 2009-10-13
Please try running memtest for a few passes.  Are you running any programs in the background e.g. compiz, drapes, boinc ? Try disabling each of them in turn.

---

### Post by highlycaffeinated on 2009-10-13
Thanks for the responses.
Nothing in Dmesg or any system logs. The system resumes like nothing happened.
Nothing unusual. The system was installed lean meaning on install I chose Command Line Install from the NetInst disk, then installed the desktop environment without all of the productivity stuff, then installed VDR (V4l2, xine-lib and xine-ui, Nvidia 190.36 driver for VDPAU), and finally XBMC. Only basic services, GDM defaults, and apache2 are running over and above the default Ubuntu stuff. Following advice elsewhere I enabled Etch backports and updated X and installed libflashplayer-nonfree, but the problem existed prior to those actions. As I mentioned, I also updated the kernel.
The hardware is up-to-date and ran just peachy in Debian. I installed Ubuntu onto a spare drive (known good) and so switched back to the Debian install - no pauses. 

I'll look to see what the manufacturer may have for updated motherboard firmware, but IIRC I updated the BIOS in it to the latest when the board arrived. It's an Asus M3N78-Em with integrated GeForce 8300 and HDMI output.

::shrugs::

I'm open to suggestions....

While typing this post I ran Memtest against all but the currently used portion of RAM and it passed w/o error. I'll run a full test when I'm home later. (at work on tunnelled ssh)

---

### Post by Kevbert on 2009-10-13
I've occasionally had random pauses with XBMC but have attributed that to a dirty DVD drive lens or disk that needs a slight clean (due to dust). Using same Nvidia driver with no problems.

---

### Post by P4man on 2009-10-13
> **highlycaffeinated said:**
> Thanks for the responses.
Nothing in Dmesg or any system logs. The system resumes like nothing happened.
Nothing unusual. The system was installed lean meaning on install I chose Command Line Install from the NetInst disk, then installed the desktop environment without all of the productivity stuff, then installed VDR (V4l2, xine-lib and xine-ui, Nvidia 190.36 driver for VDPAU), and finally XBMC. Only basic services, GDM defaults, and apache2 are running over and above the default Ubuntu stuff. Following advice elsewhere I enabled Etch backports and updated X and installed libflashplayer-nonfree, but the problem existed prior to those actions. As I mentioned, I also updated the kernel.
The hardware is up-to-date and ran just peachy in Debian. I installed Ubuntu onto a spare drive (known good) and so switched back to the Debian install - no pauses. 

I'll look to see what the manufacturer may have for updated motherboard firmware, but IIRC I updated the BIOS in it to the latest when the board arrived. It's an Asus M3N78-Em with integrated GeForce 8300 and HDMI output.

::shrugs::

I'm open to suggestions....

While typing this post I ran Memtest against all but the currently used portion of RAM and it passed w/o error. I'll run a full test when I'm home later. (at work on tunnelled ssh)

Its not gonna be a RAM problem, that wouldn't cause pauzes. It would cause crashes, freezes or reboots, but it wouldn't recover.

If the logs are clean, Im gonna have to do some pure guessing here. Try disabling cool and quiet in the bios for a starter. Other things that come to mind is a problem with the clocksource. Perhaps you can post your dmseg, even if it seems clean? I seem to recall seeing people with "tsc unstable" having similar problems. Last idea's include adding "noapic" and "nolapic" to your kernel options for no particularly good reason other than that it cures a lot of people's inexplicable problems with no real downsides :)

---

### Post by thk on 2009-10-13
I am noticing this too on some machines. Is your home directly NFS mounted?

---

### Post by highlycaffeinated on 2009-10-14
Well, it looks like it may very well have been a BIOS update issue. I pulled the latest BIOS (Which, by the way, mentioned no bugfixes, only new CPU definitions) and things seem much more stable now. I find this perplexing as this problem did not exist in Debian (with kernel 2.6.31-xx) or in XP. In the end I don't know exactly what was causing the freezes but it was either a fix in the BIOS or the fact that the new BIOS flash cleared out all of the settings back to defaults. I am 99.98% certain that I selected the same settings, but there are enough bits to flip there that I can't be absolutely certain. Either way it appears to have cleared things up. Thanks everyone for all of your help! I'd have run this in circles for quite some time before a BIOS update was all that was left!

+1 XP_convert!

-Highly

---

