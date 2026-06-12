---
title: "Very newbie login question"
date: 2006-03-10
forum: General Help
---

### Post by maikunari on 2006-03-10
Hopefully a stupidly easy question,

I've got kubuntu breezy installed finally and after booting up it asks me to login, still on the command line screen, so i give it username and password and it comes back with
(username)@kubuntu:~$

so what do i type after this to make kubuntu start up?

thanks,

maikunari

---

### Post by dermotti on 2006-03-10
first try typing gdm

if that does nothing try typing startx

if you still get nothing

type cd /etc/X11

vi xorg.conf (or nano xorg.conf its easier for nubs)

change the video drive to "vesa" and save (:wq!)

then try startx again

---

### Post by Jucato on 2006-03-10
um.. gdm is for GNOME. he's on kubuntu, so I'm presuming he's using KDE. try this
```
startx
```
If that doesn't work, try this
```
sudo /etc/init.d/kdm start
```
Btw, how did your install go? Because AFAIK, a successful normal install (not server, not expert) will put you into the graphical log-in, not at the command line prompt.

---

### Post by dermotti on 2006-03-10
Im guessing he got put into the text login prompt because something is wrong in his xorg.conf. More than likely it loaded the wrong video driver. Changing the video driver to "vesa" should resolve that so he can at least login graphically.

Ive had this issue on computers where the installer detected the wrong vid drover or it deteched an onboard controller that was disabled.

Yea GDM wont work, i assued you were using Ubuntu. KDM should tho.

edit: Fenyx we have the same amount of posts zomg!

---

