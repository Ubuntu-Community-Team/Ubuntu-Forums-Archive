---
title: "Firefox problems when using flash with sound."
date: 2009-09-19
forum: General Help
---

### Post by powerpleb on 2009-09-19
This is a rather annoying problem...

Whenever I reboot my box and fire up Firefox sound will not work on flash videos and they usually freeze after a couple of seconds.

If I then close Firefox (I need to use '$killall firefox' in order to close it properly) and restart it, the sound suddenly works.

Can anyone help me figure out is going on here?

Running Ubuntu Jaunty i686 with a Soundblaster Audigy card if that is any help.

---

### Post by jimmyhacker on 2009-09-19
SoundBlaster sound cards may not be stable on the Kernel of Jaunty.remember that jaunty is not very well tested.

---

### Post by powerpleb on 2009-09-19
> **jimmyhacker said:**
> remember that jaunty is not very well tested.

Jaunty was released nearly 6 months ago!

---

### Post by PrivateSNAFU on 2009-09-19
I have a feeling it's to do with pulseaudio or oss.  Flash, from what I remember uses oss for audio playback whilst firefox some times uses other sound servers.  I know from previous experiance that it can be fixed (I found the awnser on google but cant remember where, sorry) but I havn't had a problem whilst using 9.04.  It might be worth changing the server to oss in System>Preferences>Sound and trying it again to see if this is the problem.  

Good luck sorry I'm not too helpfull

---

### Post by harry71194 on 2009-09-28
The same thing happens to me; video seems to play fine, but if I close the tab, enjoy your Firefox locking up, and I must killall it. It is very annoying, looks like a problem with Adobe's player, [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/92207](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/92207) .... which is what you get for using lame closed-source applications... :(

---

