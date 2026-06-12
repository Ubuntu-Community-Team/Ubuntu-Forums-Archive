---
title: "Lightdm loads wrong session"
date: 2012-01-20
forum: General Help
---

### Post by m.bluemle on 2012-01-20
Hi there!

I use Xubuntu 11.10 for my HTPC with XBMC. I want that it boots direktly into XBMC when I start the HTPC. So I decided me to tell Lightdm, to start a XBMC session instead the Xubuntu session.

I edited the lightdm.conf:
```
[SeatDefaults] autologin-user=xbmc 
autologin-user-timeout=0 
user-session=XBMC 
greeter-session=lightdm-gtk-greeter
```and than create an */usr/share/xsessions/XBMC.desktop:*
```
[Desktop Entry] Name=XBMC 
Comment=This session will start XBMC Media Center 
Exec=xbmc-standalone 
TryExec=xbmc-standalone 
Type=Application
```This seems for me correct, but at the start, Xubuntu still loads the Xubuntu session! 
After many tries I did a dirty trick and copy the content of the *XBMC.desktop* into the *xubuntu.desktop* and it works!!!

why did lightdm not take the *.desktop* file that i have written in the lightdm.conf?
it always takes the xubuntu.desktop as default.

---

