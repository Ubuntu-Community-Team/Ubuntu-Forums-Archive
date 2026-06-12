---
title: "Won't boot sometimes, no sound sometimes, won't shutdown all the way sometimes"
date: 2010-09-13
forum: General Help
---

### Post by SkylinesSuck on 2010-09-13
Strange problems and I don't know if they are related.  This is Ubuntu 10.4 32 bit on a Toshiba Qosmio x505-q875 laptop dual boot with Winblows 7.  One drive bay is a 64GB SSD with windows, my root, usr, and swap partitions on it.  The other is a 1TB drive with the home partition.  

First Problem:  After the Grub menu disappears (defaulting to Ubuntu) about 25% of the time nothing happens.  No harddrive light blinking, no cursor, nothing.  Everything just stops.  I have to use the power button to reset it.  Happens several times in a row occasionally.  I've never had this happen with Windows.

Second Problem:  Sometimes Ubuntu doesn't see the sound card at all.  The speaker icon is grehyed out and when I go into sound preferences, it doesn't list any sound device at all.  Rebooting fixes it.  This happens maybe half the time.

Last Problem:  This one happens when the sound doesn't work.  When i go to shut down the system, the hibernate and suspend options are not in the shutdown menu, and when I do shut down, it only logs me off.  Even at the log on screen, if I tell the system to shut down again, nothing happens.  I can log back on it that means anything, but shutting down again has the same effect.

---

### Post by SkylinesSuck on 2010-09-14
It took me four reboots to get it started just now.  Anybody got any ideas?  I'm considering a reinstall after I figure out how not to mess with my home partition, but I'm not sure if that will fix anything.

---

### Post by SkylinesSuck on 2010-09-17
This problem is still driving me nuts.  Does this just have everybody stumped or am I asking this in the wrong section?

---

### Post by mastablasta on 2010-09-17
have you tried checking logs for any errors?
 
As for the sound - is it intel_hda? If so you might need to upgrade the ALSA.

---

### Post by SkylinesSuck on 2010-09-17
To be honest I'm not sure how to check the logs or what I'd be looking for.  About alsa, I know how to open in and play with volumes, but that's about it.

---

### Post by SkylinesSuck on 2010-09-20
Here's what I'm talking about.  Notice the greyed out start/reboot options that I got when I did the 3 fingered salute, and the lack of sound device.  No option for suspend or hibernate even displayed.

---

### Post by phazixc on 2010-09-28
Hi I'm no pro, but have been playing with ubuntu for over a year.

In regards to the sound I have had that before when I messed my sound hardware up...

You should trying install Alsa version .23 .deb

what it'll do when it installs the drivers it'll configure and load the mods so that your sound starts next time.

---

