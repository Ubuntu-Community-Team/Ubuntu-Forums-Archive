---
title: "can't get gnome-session at the startup"
date: 2010-05-03
forum: General Help
---

### Post by apshalasha on 2010-05-03
i can't start ubuntu normally. i just get a black screen and a xterm (without win decorations) section on left-top corner after starting. mouse works only on this small area where xterm is located. from xterm i can start gnome-session manually without problem. and everything seems okay. when i end this xterm session my machine logouts.

this is **.xsession-errors** file
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=tr_TR.
Start IM through /home/apshalasha/.xinput.d/tr_TR linked to /etc/X11/xinit/xinput.d/none.
```and this is **.xsession-errors.old** file
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=tr_TR.
Start IM through /home/apshalasha/.xinput.d/tr_TR linked to /etc/X11/xinit/xinput.d/none.
xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":0.0"
```i upgraded lucid from karmic, my graphic card is ati, i use win7 and ubuntu together, if it helps.

so how can i fix this problem? thanks.

---

