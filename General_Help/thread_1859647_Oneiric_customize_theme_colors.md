---
title: "Oneiric customize theme colors"
date: 2011-10-14
forum: General Help
---

### Post by garak on 2011-10-14
I just did my dist-upgrade to 11.10 and I don't find a way to customize basic theme colors (e.g. background color).
Any hint?

---

### Post by UncleVader on 2011-10-15
You have to install the gnome-color-chooser package. And run gnome-color-chooser.
That helped me to change the tooltip colors. ( White text on black background is the default !!! Who comes up with this stuff ? )

---

### Post by fragos on 2011-10-15
Someone will certainly come up with an easier way to do this but for now go to /usr/share/themes/Ambiance, the default theme. You'll need to edit three files. In the gtk-2.0 folder you need to change the the color values as in #000000. In the gtk-3.0 folder you'l need to edit colors in gtk.css and settings.ini. Change the same color values in all three files. Be sure to make backups in case things don't work properly. You'll need to reboot to get the colors to take.

---

### Post by _Impact_ on 2011-10-17
I would also like to know how to do this, as I have problems with the color of fonts.

---

### Post by fragos on 2011-10-17
Here's an example of what I changed in bold in the /usr/share/themes/Ambiance/gtk-3.0/settings.ini file.

[Settings]
gtk-color-scheme = "base_color:#ffffff\nbg_color:#**cdc3b8**\ntooltip_bg_color:#000000\nselected_bg_color:#**01b9fc**\ntext_color:#**262626**\nfg_color:#**262626**\ntooltip_fg_color:#ffffff\nselected_fg_color:#ffffff\nlink_color:#DD4814\nbg_color_dark:#3c3b37\nfg_color_dark:#dfdbd2"
gtk-auto-mnemonics = 1

---

### Post by _Impact_ on 2011-10-18
fragos, I tried what you said and still, doesn't work. Anybody can help me solve the problem?

---

### Post by fragos on 2011-10-18
Try changing themes. The one you're using was clearly modified from original.

---

### Post by _Impact_ on 2011-10-18
> **fragos said:**
> Try changing themes. The one you're using was clearly modified from original.

I tried more (GTK) themes, but now somehow the font colors reverse and the problem comes up somewhere else, like in this example:

You can't see the title of files and folders because they are the same as the background. Is there anyway to restore the defaults for themes? I think this is not a theme problem, but rather some other settings that are common for all themes.

---

### Post by _Impact_ on 2011-10-18
These are the screenshots for the different themes:

---

### Post by fragos on 2011-10-18
There's clearly something very strange that has happened to your system. At this point the only thing I can suggest is to back up your personal data and do a new clean install. On those very few occasions I've experienced white text on a white background it was always a color configuration issue that was always fixed with changing the configuration. Note that if you edited the configuration files the way I suggested you would need to reboot for the changes to take effect and also importantly, all three files referenced need to be changed to the same color values.

---

### Post by _Impact_ on 2011-10-22
> **fragos said:**
> There's clearly something very strange that has happened to your system. At this point the only thing I can suggest is to back up your personal data and do a new clean install. On those very few occasions I've experienced white text on a white background it was always a color configuration issue that was always fixed with changing the configuration. Note that if you edited the configuration files the way I suggested you would need to reboot for the changes to take effect and also importantly, all three files referenced need to be changed to the same color values.

fragos, I just did what you said and still... doesn't work. Yet when I log with a guest account, the colors are fine. Is there anyway I can edit/reset the theme settings?

Thanks

---

### Post by fragos on 2011-10-22
Click icon in upper right hand corner and select "System Settings" and then "Appearance." On the bottom you can select another offered "Theme". To edits individual colors is more involved and requires making changes to in case of Ambiance, to 3 files.

---

### Post by _Impact_ on 2011-10-23
> **fragos said:**
> Click icon in upper right hand corner and select "System Settings" and then "Appearance." On the bottom you can select another offered "Theme". To edits individual colors is more involved and requires making changes to in case of Ambiance, to 3 files.

I changed the color values as showed by you in that example in bold - in all 3 files: 

In the folder gtk-2.0 changed the values in file gtkrc
In the folder gtk-3.0 changed the values in files gtk.css and settings.ini

---

