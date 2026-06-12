---
title: "VLC audio is stuttering on Meerkat"
date: 2011-01-09
forum: General Help
---

### Post by meddyuk on 2011-01-09
Hi there.  I wondered if anyone could offer a solution to my problem. I've just installed VLC medi player and have tried to play a video that i know works. The video side of life is fine, infact im more than happy with it, however, the audio is very stuttery and jumpy.  I googled the problem and one answer was to go to preferences>audio outputs and to change from default to UNIX OSS. I did this however there was no change.  Another solution was Workaround for glitchy (crackling, skipping) audio is to open: /etc/pulse/default.pa  Find the line that looks like this and add "tsched=0". Code:  load-module module-udev-detect  It should look like this:  load-module module-udev-detect tsched=0  Save and reboot (or just log out).   However i did this too and the problem is the same. Any tips?  Meddy.

---

### Post by sat_e_llite on 2011-01-09
> **meddyuk said:**
> Hi there.  I wondered if anyone could offer a solution to my problem. I've just installed VLC medi player and have tried to play a video that i know works. The video side of life is fine, infact im more than happy with it, however, the audio is very stuttery and jumpy.  I googled the problem and one answer was to go to preferences>audio outputs and to change from default to UNIX OSS. I did this however there was no change.  Another solution was Workaround for glitchy (crackling, skipping) audio is to open: /etc/pulse/default.pa  Find the line that looks like this and add "tsched=0". Code:  load-module module-udev-detect  It should look like this:  load-module module-udev-detect tsched=0  Save and reboot (or just log out).   However i did this too and the problem is the same. Any tips?  Meddy. It has something to do with Pulseaudio, having that removed doesn't seem to help too.

Don't remove it, it's a bit tedious to re-install.

---

### Post by Roasted on 2011-01-16
Also curious if anybody can bring up any fixes for this. I installed 10.10 on a netboook (regular gnome edition) and some files I play have the choppy audio. I tried movie player and they work perfectly fine, therefore making it obvious it's VLC's problem.

What can be done to fix this? I know that even though it's a netbook I should have the resources. I barely use up 200mb of RAM to run Ubuntu from a fresh start.

---

