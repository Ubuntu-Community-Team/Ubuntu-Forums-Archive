---
title: "Where are icons stored for a  launcher?"
date: 2009-09-14
forum: General Help
---

### Post by x C0MMAND0 x on 2009-09-14
I'm trying to add custom icons to Cairo-Dock.  For example, I add pidgin, but I don't like the icon associated with it with that theme.  I try to navigate to find the pidgin icon, but I don't know where it is.

I am able to drag the application launcher to my desktop and the icon is correct.  See attached screenshot.  I like the image shown in the screen shot, so I click on it to try to find out what directory its in, but it just brings be to my home/user folder... I checked in /home/user/.purple for this particular icon, but it wasn't there.  Where are they all located?  My /home/user/.icons folder is empty too..

---

### Post by x C0MMAND0 x on 2009-09-14
attached image

---

### Post by CoolHand on 2009-09-14
I don't think the above edit capture was very clear.  If you want the actual filesystem location look in /usr/share/pixmaps.  If you are using KDE try under /usr/share/icons

---

### Post by drs305 on 2009-09-14
That particular icon is located at:
/usr/share/icons/hicolor/48x48/apps/pidgin.png

Here's a GUI way of finding it. Make a custom panel launcher. Type in the standard run command, such as "pidgin". If Ubuntu recognizes it, it will put the standard icon in the icon window. Then double-click the icon to find the address.

Some of the icons Pidgin uses are in:
/usr/share/pixmaps/pidgin


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by x C0MMAND0 x on 2009-09-14
Thank you!

---

### Post by fabounet on 2009-09-15
in the config panel of the dock, just indicate the icon theme you want to use (in the "Icon" module), and disable the use of local icons (they are in ~/.config/cairo-dock/current_theme/icons)
or use the local icons, and put there the icons you want.

---

