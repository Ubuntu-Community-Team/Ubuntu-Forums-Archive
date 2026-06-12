---
title: "I think Update Manager is feeding me duplicate/unnecessary updates."
date: 2009-11-18
forum: General Help
---

### Post by anthony62490 on 2009-11-18
Running Ubuntu 9.4

It started when I updated Firefox 3.0 to Firefox 3.5 (Shiretoko) Update manager started giving me updates for Firefox 3.0 (no longer installed). It gives me the same updates every day even though I have it set to check for updates every week. I ignored it at first, but now the list is getting bigger. It added Virtualbox (using Virtualbox version 3.0.8 r53138 ) updates every day along with Pulseaudio and Totem (which has been installed for a long time now)

The full list of updates for today is:

Recommended:
libpulse-browse0
libpulse-mainloop-glib0
libpulse0
libpulsecore9
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseaudio-module-x11
pulseaudio-module-zeroconf
pulseaudio-utils
totem
totem-common
totem-gstreamer
totem-mozilla
totem-plugins

Other:
firefox
firefox-3.0
firefox-3.0-gnome-support
firefox-3.5
firefox-3.5-branding
firefox-3.5-gnome-support
firefox-gnome-support
virtualbox-3.0
xulrunner-1.9.1
xulrunner-1.9.1-gnome-support

Its starting to become a hassle. Any ideas on how I can convince my PC if I already HAVE these packages?

---

### Post by P4man on 2009-11-18
you may have those packages, but not the latest updates of those packages, which is what you're being presented. As for ff 3.0, I bet you still have it.

---

### Post by SirBismuth on 2009-11-18
Are you SURE FF 3.0 is not installed, as 3.5 (Shiretoko) uses different repositories.  I added the Daily Build PPA to my Software Sources in 9.04, to get 3.5.  While I transferred my settings and bookmarks to 3.5, 3.0 was still there and I could use it if I chose to, as they are installed side-by-side then.

Haven't tried this since installing 9.10, as 3.5 is already in the repos, though.

B

---

### Post by 3rdalbum on 2009-11-18
Firefox 3.5 installs alongside 3.0; so you've probably got both.

Do you get any error messages if you run the upgrade on the command line?

```
sudo apt-get dist-upgrade
```

(this command upgrades the current system; it doesn't upgrade you to a new version of Ubuntu).

---

### Post by garvinrick4 on 2009-11-18
9.04 you get both and 9.10 you get just firefox 3.5

It was just called Shiretiko in 9.04 on the upgrade from 3 to 3.5

Was then anyway.

---

### Post by patep34 on 2009-11-25
I'm kind of having the same problem... but I went ahead & did the updates anyway. My version of Shiretoko got updated but all my other versions of Firefox didn't.

I seem to have Firefox 3.5.2 & 3.5.3 on my machine, as well as Shiretoko (3.5.5). I finally got the 2 Firefoxes out of my applications menu so I wouldn't accidentally go to them, but can I (or should I) get rid of them completely? The Synaptic Package Manager seems scary since all the packages seem interwoven; but the Add/Remove Applications app seems like it could do the trick - should I do it & just keep Shiretoko?

Thanks in advance for helping a newbie!

Sticking with 9.04 for a little while,
Patep

---

