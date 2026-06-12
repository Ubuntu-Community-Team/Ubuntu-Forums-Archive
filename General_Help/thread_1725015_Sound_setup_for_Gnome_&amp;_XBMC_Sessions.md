---
title: "Sound setup for Gnome &amp; XBMC Sessions"
date: 2011-04-09
forum: General Help
---

### Post by jingo_man on 2011-04-09
the primary use of the server is as a HTPC running XBMC (XBMC-Standalone) which runs in its own "desktop session" (is that the correct wording?)

this uses ALSA and works fine if PulseAudio isn't running. if PulseAudio is running, the audio fails to initialise when playing anything back. "sudo pulseaudio -k" fixes this.

occasionally, i exit this full-screen app and login into the Gnome desktop session, i.e. to play back some other stuff like flash video that i cannot get inside XBMC itself. when i do this, i think the system uses PulseAudio. this then breaks the sound when i want to return to xbmc, even following a reboot.

basically, i now have a system that i am unable to get any desktop sounds in the firefox browser or vlc when playing stuff through it.

i tried to remove PulseAudio from starting at boot with the command "sudo update-rc.d pulseaudio disable 2 3 4 5". after a reboot, its still there!! wtf!?!??

> ps auxwww | grep -i pulse
1000      1537  0.7  0.1 160424  4936 ?        S<sl 08:44   0:09 /usr/bin/pulseaudio --start --log-target=syslog

can anyone help me with my setup please? what should i be running, PulseAudio or ALSA? has PulseAudio been fixed/improved from earlier versions? does it run with XBMC (10.1) now? is it running better with Lucid (10.04 is version i am running)?

many thanks

jingo_man

---

