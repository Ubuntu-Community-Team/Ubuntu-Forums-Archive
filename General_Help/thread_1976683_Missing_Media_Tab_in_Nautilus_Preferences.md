---
title: "Missing Media Tab in Nautilus Preferences"
date: 2012-05-09
forum: General Help
---

### Post by layolayo on 2012-05-09
Hi - using 12.04

Does anyone know where the Media tab has gone from Nautilus' preferences?

I have ended up using gconf-editor to reset settings. But the media tab was useful, also I have read that a Removable Media setting should be in System Settings -> Hardware...? I do not have this

[edit: the problem I am having is when connecting my Android phone, RhythmBox opens automatically, I do not want it to. Unfortunately changing those settings in gconf-editor - Nautilus, have done nothing. I have removed all references to RhythmBox out of ~/.local/share/applications/mimeapps.list . However it's still opening]

thanks

Layolayo

---

### Post by layolayo on 2012-05-09
Ok - so mimeapps.list doesn't seem to do anything.

However in 12.04:

System Settings -> System -> Details -> Removable Media

All these settings were showing "Ask what to do" - even though RhythmBox was opening automatically.

I changed these to "Do Nothing"

Success-O

Now if I put back to "Ask what to do" - the box for asking what to do comes up, so something was reset. Not sure where, but it would be nice to know.

Layolayo:guitar:

---

