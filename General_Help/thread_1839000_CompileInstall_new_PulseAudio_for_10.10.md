---
title: "Compile/Install new PulseAudio for 10.10"
date: 2011-09-04
forum: General Help
---

### Post by dardack on 2011-09-04
Ok so I dropped back to 10.10.  I couldn't stand the unity interface and the changes in certain things that don't work in Gnome 2.0 anymore with 11.04 (I dread the day I have to upgrade to 11.10+, with either gnome 3 or unity).

Anyways, I downloaded alsa-plugins 1.0.24 and Pulse Audio 0.9.23.  I compiled/sudo make installed.  Alsa-plugins seem to install correct directory, but pulse seems to put it in some usr/local/lib instead of usr/lib.  

So I did a sudo find -name (name of pulse lib) and found where the system stored the lib/bin/etc/etc. files.  I then did a mkdir pa.old (in each fold that had PA files), mv pafiles pa.old, then cp the files from the compiled PA folder.

I then rebooted.  no sound.  The little sound icon showed muted, and when I clicked on it couldn't bring up any options.  I then logged out, then back in, and no sound but could bring up options, went to the Hardware tab, changed from Duplex to off back to duplex had sound.

Opened pulseaudio applet, checked manage, says server is 0.9.23, Nice.  So I reboot, same thing.

Everytime I reboot, I have to log out then log back in, change the HW option and back again, to get sound.  Then it works.

Is there a better way to do this?  Do I need something other then the PulseAudio source?  (ie is there some other package I need to compile/install along side PA to make it work seemlessly?) is there some conf file I have to change?

There are few reasons I'm doing this, since I won't upgrade to 11.04/11.10 at this point, and wine has gone above 1.3.24 (the last version to support wine-pulse patch).  Wine then uses an alsa plugin to communicate with the pulse server.  The Pulse server in 10.10 is too old for wine (1.3.27 at least) because of new API calls (or something), and the  Pulse/Alsa-plugins have a bug in 11.04 (that is from the launchpad bug fixed for 11.10 but will not be backported (again because of new API's or something)) that after a time the sound will stop from the alsa-plugin.


EDIT:  Also I've also messed something up because PULSE_ContextStateCallback Context failed: Connection refused for a wine with wine-pulse installed.

---

