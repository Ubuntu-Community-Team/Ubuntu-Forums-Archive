---
title: "GUFW Won't Use GTK2 Themes -- Why?"
date: 2010-06-14
forum: General Help
---

### Post by DasFox on 2010-06-14
I'm running another distro but thought I'd ask here since ufw/gufw is typically on Ubuntu and Ubuntu based distros, but I wanted a simple firewall so I installed it.

But GUFW won't use any GTK2 themes I have installed.

I have a .gtkrc-2.0 file I use by hand to switch them and all my other apps switch to the themes, but GUFW won't.

Why Won't GUFW change to using a gtk2 theme? All it does it looks like a GTK1 app instead. :(

Here's my .gtkrc-2.0 file:

```

#
# Select GTK+ Themes
#


gtk-theme-name="Equinox"
#gtk-theme-name="Laza"
#gtk-theme-name="Mire-v2_Grey"
#gtk-theme-name="Moka"
#gtk-theme-name="The-days-of-grays"


#
# Select GTK Fonts
#


#gtk-font-name="Bitstream Vera Sans 8"


#
# Select GTK Icons
#


#gtk-icon-theme-name="BRIT-ICONS"
gtk-icon-theme-name="SimplyGrey"

gtk-icon-sizes="gtk-menu=32,32:\
                gtk-button=32,32:\
                gtk-small-toolbar=32,32:\
                gtk-large-toolbar=32,32:\
                gtk-dnd=32,32:\
                gtk-dialog=32,32"
gtk-toolbar-style = GTK_TOOLBAR_ICONS

```

---

### Post by marquinos on 2010-06-14
Hi! I'm a Gufw developer.
Could you attach a screenshot, please?
Gufw uses Glade for the GUI.
Best regards! :)

---

### Post by marquinos on 2010-06-14
I see the bug :P [https://bugs.launchpad.net/gui-ufw/+bug/593626](https://bugs.launchpad.net/gui-ufw/+bug/593626)
I will continues there :)

---

### Post by DasFox on 2010-06-14
**Here's a screenshot:**


[[IMG]http://img229.imageshack.us/img229/3136/gufw.jpg[/IMG]]("http://img229.imageshack.us/i/gufw.jpg/")

---

