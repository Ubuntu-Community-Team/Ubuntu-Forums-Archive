---
title: "I managed to screw up my rc.d settings help!"
date: 2009-08-17
forum: General Help
---

### Post by Pitboss on 2009-08-17
Hi, as the title says I managed to screw my init scripts up. So now I'm getting some weird messages in the syslog like:

pulseaudio[3880]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.

And when I reboot it says something that I can't write down but starts with the following:

nm-system-settings SCPLUGIN bla bla...

I thing that this is because I used update-rc.d and chkconfig in wrong way and scrambled the default numbers of the scripts in the different runlevels. So if someone can post his or tell me how I can get back my default configuration I'll be very grateful.

---

