---
title: "Drapes not loading on start"
date: 2009-12-30
forum: General Help
---

### Post by Gorlist on 2009-12-30
Good morning, have problems with Drapes failing to load on start, checked the logs and its come back with: 

```
Dec 30 08:16:05 my-desktop gnome-session[1777]: WARNING: Could not parse desktop file /home/my/.config/autostart/drapes.desktop: Key file does not have key 'Type'
Dec 30 08:16:05 my-desktop gnome-session[1777]: WARNING: could not read /home/my/.config/autostart/drapes.desktop
```

Any suggestions, or is their an alternative to drapes (other than that wallpaper try app)? 

Best Regards,

---

### Post by rabdoel on 2010-01-09
you will need to edit the following file 

home/username/.config/autostart/drapes.desktop

and add the following line to the bottom of the page 

"Type=Application"

taken from - [https://bugs.launchpad.net/drapes/+bug/292051](https://bugs.launchpad.net/drapes/+bug/292051)

I had this problem in karmic koala 9.10

so press alt+F2 .. in the box that appears type "gnome-terminal" and press run

now in the terminal screen type
sude gedit  home/username/.config/autostart/drapes.desktop  ( where username is your own username) 

desktop.drapes file will come up and add the following on the last line 
"Type=Application"

press save and now logout and log back in again .. that should fix it

---

### Post by Gorlist on 2010-01-09
thank you for that, working perfectly - you don't happen to know if its possible to hide the icon that appears in notification area?

Regards!

---

### Post by rabdoel on 2010-01-09
nope sorry .. dont know how to do that .. maybe someone else can help

---

### Post by Meghnaad on 2010-02-13
Thank you !
Worked for me !(ubuntu 9.10 32 bit)

This Community Rocks

---

