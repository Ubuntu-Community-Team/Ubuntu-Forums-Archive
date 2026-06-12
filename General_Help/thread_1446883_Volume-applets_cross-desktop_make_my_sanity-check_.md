---
title: "Volume-applets cross-desktop make my sanity-check fail."
date: 2010-04-04
forum: General Help
---

### Post by Silent Warrior on 2010-04-04
Bugger me if I haven't three desktops installed - Gnome, KDE, and Xfce. And it kind of seems they all behave differently with regards to volume-settings when I shut them down.
Gnome is the main desk, so let's consider that normal. Shutting down in KDE, and logging into Gnome on the next boot will typically result in muted sound (fixed by changing the volume, go figure). Shutting down from Xfce (well, both KDE and Xfce drop out to GDM first, but you get the idea) and logging into Gnome often requires substantial fiddling on my part to get sound back. Possible, but something of a bother.
I use PulseAudio in Gnome, and while it's available in KDE, KMix is sort of central and seems to be the main culprit of just about anything I perceive as a sound-issue coming out of KDE into Gnome. I don't know what's going on with Xfce... (I'm just poking on the surface, testing it for a bit. It's not some serious productivity-desktop presently.)

I assume this is to do with muting something or other. Is there some way I can make them all behave the same, i.e. not muting Gnome all the beeping time? :-({|=

---

### Post by NightwishFan on 2010-04-04
I am not sure that is normal behavior, perhaps reinstall alsa-utilities.
```
sudo apt-get install --reinstall alsa-utils
```

Then run this and configure your volume.
```
alsamixer -c0
```

---

### Post by Silent Warrior on 2010-04-05
Done. I have yet to log into Gnome again, but I suppose it doesn't hurt to add that there's never any problem going from Xfce to KDE.

I logged into KDE to do some superficial testing, and unset the option in KMix to 'Restore volume levels on startup'. I then rebooted and logged into Xfce, where the PulseAudio volume-applet showed as unmuted. I don't remember if this is a change from the usual behaviour, but I'll know when I check out Gnome again.

[Update]
Okay, went from Xfce into Gnome, no adjustments required. I'll just monkey around some more before I test going from KDE to Gnome.

[Update 2]
And KDE to Gnome tested, no adjustments required to get sound. Not sure whether it was jiggling ALSA's handle or the option in KMix, but I'm marking this as solved. Whee!

---

