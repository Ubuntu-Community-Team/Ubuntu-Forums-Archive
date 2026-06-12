---
title: "no sound in LXDE(desktop with ubuntu)"
date: 2009-10-21
forum: General Help
---

### Post by xxterry1xx on 2009-10-21
i installed LXDE and there is no sound and i always have to start up gnomes network manager


kk i fixed the sound something happend when i installed LXDE or i accidently hit the mute button on my keyboard(i doubt it works anyways cause its a microsoft keyboard it relies on intelltype drivers for windows for the mute buttons and that to work)

---

### Post by neeraj2608 on 2010-02-25
> i always have to start up gnomes network manager

Add the line "@nm-applet" to the file /etc/xdg/lxsession/LXDE/autostart

---

