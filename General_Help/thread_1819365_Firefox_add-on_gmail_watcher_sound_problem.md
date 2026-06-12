---
title: "Firefox add-on gmail watcher sound problem"
date: 2011-08-06
forum: General Help
---

### Post by trinux_bc on 2011-08-06
I posted this on askubuntu, but I thought I'd post it here too just in case.

I'm using a firefox extension called gmail  watcher([https://addons.mozilla.org/en-US/firefox/addon/gmail-watcher/](https://addons.mozilla.org/en-US/firefox/addon/gmail-watcher/))  and for some reason it won't play a custom sound notification. I've got  it working on a Mac and in PCLinuxOS, but for some reason Ubuntu 11.04  won't play the .wav file that the extension needs. I tried to set up  custom sound notification in thunderbird and it wouldn't work there  either. Both firefox and thunderbird will play the system sound.  Restricted extras are installed, sound works fine for everything except  these email notifications. Any ideas? Any one else having similar  issues? Thanks

trinux_bc

---

### Post by trinux_bc on 2011-08-07
Got it working by installing the vlc plugin.

trinux_bc

---

### Post by lovinglinux on 2011-08-07
> **trinux_bc said:**
> Got it working by installing the vlc plugin.

trinux_bc

I don't recommend the VLC plugin. It is not good. Get rid of it and install gecko-mediaplayer or totem. At least try to disable it in the add-ons manager, otherwise it will probably take over multimedia content.

---

### Post by trinux_bc on 2011-08-07
I had tried gecko-mediaplayer and it wasn't working for some reason, that's how I ended up posting here and trying vlc. Just tried gecko-mediaplayer again it's working now, something must've gotten messed up somehow the first time, so the vlc plugin is gone. Thanks for the reply.

trinux_bc

---

