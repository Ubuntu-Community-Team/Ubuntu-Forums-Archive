---
title: "Change Menu Bar Icon?"
date: 2010-07-16
forum: General Help
---

### Post by Cam! on 2010-07-16
I use the Elementary GTK theme, and I'd like to replace the "E" at the upper-left hand with my custom Ubuntu logo. However, when I extract the icon to the proper directory, and replace all files, nothing happens. I delete the cache, kill and restore the panel via Terminal, and rebuild the cache, to no avail.

---

### Post by ajgreeny on 2010-07-16
Normally you do this with gconf-editor.  navigate to apps-panel-objects and find the menu object, then change the custom_icon entry to what you want, and put a tick in the use_custom_icon box as in my screenshot.

The icon must be a png file, I think, though I have not tried others, but the size does not seem to matter too much as it is resized to fit the panel.

---

### Post by Cam! on 2010-07-16
I tried. It still doesn't work. :(

---

### Post by irw on 2010-07-26
[Ubuntu-Tweak]("http://ubuntu-tweak.com") will change it for you - although you may need to resize it to fit.

---

### Post by Cam! on 2010-08-09
Where's the option to change it via Ubuntu Tweak?

---

### Post by irw on 2010-08-09
Ubuntu-Tweak: Look for 'GNOME settings' in the Desktop section in the left pane

---

### Post by ParadoxBlue on 2011-01-13
> **irw said:**
> [Ubuntu-Tweak]("http://ubuntu-tweak.com") will change it for you - although you may need to resize it to fit.
Yes but what's the trick to get it to change with Tweak? After I change the graphic and choose 'yes' to make the changes take effect immediately my panels disappear and don't come back until I reboot by pushing the restart button on my system and no changes are made. If I choose 'no' to delay the change then I quit Tweak and restart my system from the panel menu and still no change. Any advice?

---

