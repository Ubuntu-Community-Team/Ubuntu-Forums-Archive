---
title: "Change screen saver"
date: 2010-05-08
forum: General Help
---

### Post by SpaceBison on 2010-05-08
[http://www.freesoftwaremagazine.com/columns/customizing_your_screensaver]("http://www.freesoftwaremagazine.com/columns/customizing_your_screensaver")

I want to change the image in the floating ubuntu screensaver in 10.04 back to what was used in 9.10. I used the guide above but overwrote the old file instead of creating a new one. When I click on it, it shows the image I specified, but in the screensaver manager under system>preferences it still plays the new logo, not the old one. I've restarted my computer and such but no luck. Is there something else that needs to be changed?

> [Desktop Entry]
Name=Floating Ubuntu
Comment=Poop the GNOME foot logo around the screen
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/floaters /home/matt/Pictures/Wallpaper/ubuntu500.png
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/floaters
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver

---

### Post by SpaceBison on 2010-05-08
..

---

### Post by SpaceBison on 2010-05-10
Hmm, it seems to have worked itself out :)

---

