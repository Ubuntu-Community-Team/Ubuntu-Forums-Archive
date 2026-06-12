---
title: "Installing from the live CD:"
date: 2006-06-06
forum: General Help
---

### Post by deb2006 on 2006-06-06
When installing from the live CD it is impossible to correct the resolution of the graphics adapter. Even afterwards it is impossible to do so. In order to be able to change the resolution I had to tweak xorg.conf which was ok for me - but it's neither ok nor possible for a new Ubuntu user.

In short: I liked the old installer much better.

---

### Post by ifokkema on 2006-06-06
[QUOTE=deb2006]When installing from the live CD it is impossible to correct the resolution of the graphics adapter. Even afterwards it is impossible to do so. In order to be able to change the resolution I had to tweak xorg.conf which was ok for me - but it's neither ok nor possible for a new Ubuntu user.

In short: I liked the old installer much better.[/QUOTE]

I guess it's always a matter of pleasing as many as possible. I kinda liked the idea of having a combined Live/Install CD and really loved the graphical interface. I think it makes the transition from Windows easier for people who want to give Linux a try on their HD.

By the way, I had no problem with my resolution but I guess running
```
sudo dpkg-reconfigure xserver-xorg
```
is a bit easier?

Ivo

---

### Post by grsing on 2006-06-06
I do wish there was an option on the CD to just use the text-based installer.  If I know I'm going to install and don't need/want to play around with the LiveCD, I don't really want to have to wait for all the prettiness to load.  I suppose that's probably available on the "Alternate" CD (with the OEM tools, I would guess), but it can't really take up so much space it couldn't be an option on the main CD, I wouldn't think.  Though I definitely support the combined Live/Install, too, especially for new users.

---

### Post by joske on 2006-06-07
If you download the DVD, you can choose live CD installer or text-base one.

---

