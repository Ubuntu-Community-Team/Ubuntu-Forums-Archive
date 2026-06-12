---
title: "Panel applet icon location (so i can change it)"
date: 2010-07-24
forum: General Help
---

### Post by HelloIndustries on 2010-07-24
Hi all.

I've done a bit of googling, and some searching around here, but to no avail, so i'm going to ask you lovely lot where i can find the icon location/s for:

[IMG]http://i901.photobucket.com/albums/ac212/helloiamdene/powerbutton.jpg[/IMG]

I'm using Ubuntu 10.04 with Gnome

---

### Post by Vaphell on 2010-07-24
icons usually are located somewhere in /usr/share/icons/
you need to look into gnome dir and theme directories. This one should be the one you want
/usr/share/icons/Humanity/actions/<icon_size>/system-shutdown.svg though there may be copies floating around.

usually icons used by panel applets are in 16-24px range and touching only these should do the trick, unless you want seamless experience for all sizes - then replacement for all is required

---

### Post by HelloIndustries on 2010-07-24
> **Vaphell said:**
> icons usually are located somewhere in /usr/share/icons/
you need to look into gnome dir and theme directories. This one should be the one you want
/usr/share/icons/Humanity/actions/<icon_size>/system-shutdown.svg though there may be copies floating around.

usually icons used by panel applets are in 16-24px range and touching only these should do the trick, unless you want seamless experience for all sizes - then replacement for all is required

That did the trick, thanks :)

---

