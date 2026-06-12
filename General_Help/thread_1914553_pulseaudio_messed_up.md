---
title: "pulseaudio messed up"
date: 2012-01-24
forum: General Help
---

### Post by bobman321123 on 2012-01-24
I did some stuff with pulseaudio, and managed to mess it up. It isn't a simple case of turning it back on, since that actually turns sound off... go figure.
Anywho, how would I restore pulseaudio completely to how it was at install?

---

### Post by hwttdz on 2012-01-24
purge and reinstall, you may also have to delete your user config files, at least
~/.pulse-cookie
~/.pulse
there may be more.

Also, I realize I was brief, purge refers to a specific command not just the act of removing in general.  Specifically

apt-get purge pulseaudio 

(and I'd probably purge everything related).  Purge differs from remove in that it removes config files as well.  Installing after purge will get you unmodified configuration files.

---

