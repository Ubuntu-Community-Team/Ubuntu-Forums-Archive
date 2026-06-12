---
title: "Fresh install Lucid 10.0.4 unstable / volume doesn't control sounds"
date: 2012-03-21
forum: General Help
---

### Post by atomicblue on 2012-03-21
I installed a fresh install of 10.04.4 because the system became so unstable after a borked kernel install.  Update Manager installed a kernel halfway and that was the beginning of my problems.

After a fresh install, I installed Chrome and Adobe Flash (beta) 11.1 r102 because the "stable" version from the repos would not play sound for Youtube videos.  The most recent version of wine offered from the repos complains that I need to update my ALSA, so I added ppa:team-iquik/alsa to my Software Sources. 

Even though team-iquik has compiled a 1.0.24 version of ALSA for 10.04 which it installs, but the version number never updates in the system:

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.


Now, I can have music playing loudly while I have all system sounds muted from the volume control.  The entire system locks up whenever I try to watch a Youtube video to the point the NUMLOCK key does not change the indicator light on the keyboard.  I have a native Linux game that is correctly muted and appears to be controlled by the Sound Preferences volume / mute, but Skype and any programs / sounds I run through wine sound really scratchy.  

Browsing the web using Chrome or Firefox are super slow.  (I'm plugged directly into the router across the room, which is next to the cable modem.)

Could someone offer any assistance to work to stabilize this system before I throw this computer out of the window?

---

### Post by atomicblue on 2012-03-21
At this point it doesn't really matter.  I had Update Manager pop up and say there was a new kernel to install, which I did.  

When I rebooted this hosed the system and it's sitting at grub rescue>.   I'm almost to the point that I'm over Ubuntu.

---

