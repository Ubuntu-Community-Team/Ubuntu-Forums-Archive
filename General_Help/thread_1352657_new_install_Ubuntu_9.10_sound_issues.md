---
title: "new install Ubuntu 9.10 sound issues"
date: 2009-12-11
forum: General Help
---

### Post by 37fleetwood on 2009-12-11
I just installed Ubuntu 9.10 on a brand new computer. I set it up dual boot with Windows XP. when I finished the install the sound worked in Ubuntu but not in XP. I used Ubuntu to download the drivers for windows and logged out and booted to XP, installed the driver which worked fine. when I rebooted into Ubuntu and started to install the Applications I like I noticed that somewhere along the way I have lost the sound. I'm kinda doubting it can have anything to do with installing the sound drivers in XP but I wanted to list everything. I'm guessing I lost it somewhere in the process of installing the apps. how can I figure this out? someone please help me figure this out. my next step is going to be to start over and just re-install everything which is fine since I haven't actually done much with it yet I just hoped to save the time.
thanks in advance,
Scott

---

### Post by 37fleetwood on 2009-12-11
well somehow I got it fixed. I just built the system reusing my old case and aparently the front panel sound hookup isn't compatible. I shut down the computer, and unhooked it and rebooted and the sound came back on.
now I'm confused, if it was the front panel hookup, how did it work before? if it wasn't how is it working now?:-k

---

### Post by 37fleetwood on 2009-12-14
update!
I logged into the Kubuntu desktop and the sound went away again. I logged back into Gnome and sure enough no sound.
 I logged out and went back to KDE to see what was going on and discovered it was trying to use the tv tuner card as a sound card. I shut the computer off and took out the tuner and rebooted into KDE and it works fine. back into Gnome and sounds back. I guess if I ever want to use the tuner card, I'll need to figure it out. funny thing, I never had any issue in 8.10 or 9.04 with this. maybe as 9.10 updates, this will be resolved.

---

### Post by 37fleetwood on 2009-12-17
I may have been too hasty in pronouncing this issue resolved.
the issue manifests when I log out of XP using "restart". if I shut down, then restart, it seems more inclined to come up with sound:confused:

---

### Post by stevemot on 2009-12-17
This sounds like a card firmware issue. I don't think you said what type of sound card you have, but many peripheral cards these days rely on the operating system to upload their firmware onto the card at boot time, rather than it being stored in permanent memory (ROM or Flash) on the card.

Its possible that your Windows sound driver installs some firmware on the card that is not compatible with the linux drivers. If you then restart and boot into Ubuntu without the power going off, sound will not work in Ubuntu. However if you shut down, then power up straight into Ubuntu, the XP driver's firmware is not there, the linux driver can then initialise normally, and everything works.

Just a theory, but you might want to try uninstalling the XP sound card driver to see if that fixes the Ubuntu sound issues.

Steve M

---

