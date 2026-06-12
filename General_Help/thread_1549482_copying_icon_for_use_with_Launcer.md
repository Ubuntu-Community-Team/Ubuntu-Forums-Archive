---
title: "copying icon for use with Launcer"
date: 2010-08-09
forum: General Help
---

### Post by 3pinner on 2010-08-09
I just installed a program in WINE, that put a launcher on my desktop with a nice graphic.
I've installed a Launcher in the applications menu for the new program, but I would like to have that Launcher have the same graphic as the one on my desktop.
How do I do this?
Thanks

---

### Post by dmillerw on 2010-08-09
Assuming you're using Gnome, right click on your menu bar, should be an option to "Edit Menus"

Find the application you want by navigating to the proper folder in the sidebar, simply click the launcher you want to change, and click Properties, change the icon the same way you normally do.

[IMG]http://i37.tinypic.com/zvr5vq.png[/IMG]

---

### Post by 3pinner on 2010-08-09
Actually I just figured out where to find the icon file I needed.
It lives in a different folder than the icons Ubuntu would normally use.

it was in the .local/share/icons folder. I copied it to the 
usr/share/icons/hicolor/scalable/apps folder where all the other apps icons live, then did as you suggested and I have my custom icon.

---

