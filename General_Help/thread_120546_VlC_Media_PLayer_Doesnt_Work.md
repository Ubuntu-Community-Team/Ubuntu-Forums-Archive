---
title: "VlC Media PLayer Doesnt Work"
date: 2006-01-22
forum: General Help
---

### Post by nominal on 2006-01-22
Vlc media player wont work. I d/l off of automatix and i tried opening a song on it, and it wont open. It wont play cds or anything.

---

### Post by bloodborne on 2006-01-22
Did you make sure to install the multimeda codecs from Automatix as well?

---

### Post by nominal on 2006-01-23
[QUOTE=bloodborne]Did you make sure to install the multimeda codecs from Automatix as well?[/QUOTE]

Yup. But now that we're on Automatix, if i try instaling mozilla plugins from it...it d/l and says it installs but doesnt show up on Mozilla...I can d/l other things form automatix so....

---

### Post by arnieboy on 2006-01-23
[QUOTE=nominal]Yup. But now that we're on Automatix, if i try instaling mozilla plugins from it...it d/l and says it installs but doesnt show up on Mozilla...I can d/l other things form automatix so....[/QUOTE]
when u type the following in your firefox address bar > about:plugins 
it will show you what plugins u have installed (which also includes what automatix installs) for firefox.
as for VLC media player, you probably need the non-free audio and video codecs. I will also suggest you use totem-xine rather than vlc.

---

### Post by nominal on 2006-01-23
[QUOTE=arnieboy] I will also suggest you use totem-xine rather than vlc.[/QUOTE]

in that case. how do i un-install vlc

---

### Post by arnieboy on 2006-01-23
[QUOTE=nominal]in that case. how do i un-install vlc[/QUOTE]
```
sudo apt-get remove vlc vlc-plugin-arts wxvlc
```

---

