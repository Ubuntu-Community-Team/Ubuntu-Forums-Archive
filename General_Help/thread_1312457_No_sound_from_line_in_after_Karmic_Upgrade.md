---
title: "No sound from line in after Karmic Upgrade"
date: 2009-11-03
forum: General Help
---

### Post by Cappientes on 2009-11-03
After upgrading to Karmic it appears the line in is muted? I use my line in for sound coming from my other PC which means I can only get sound from my linux box at the moment.

Has anyone else come across this? Has anyone got a suitable fix?

I use to just unmute it in under Sound > Preferences but this seems to be a new application in Karmic.

Cheers,

C

---

### Post by P4man on 2009-11-03
try ```
alsamixer
``` in a terminal. Or if you prefer a gui, install gnome-alsamixer

---

### Post by Cappientes on 2009-11-03
Awesome thanks.

Installed gnome-alsamixer > Applications > Sound and Video > GNOME ALSA MIXER > unmuted line > increased volume of line

I'll go and see if a bug has been filed against this.

Cheers,

C

---

### Post by P4man on 2009-11-03
Its not a bug.. its just a sorely missing feature. 
They simplified the pulse audio settings, but a bit too much.

---

