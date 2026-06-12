---
title: "KDE overriding Gnome font settings"
date: 2006-04-04
forum: General Help
---

### Post by Burgresso on 2006-04-04
I've recently installed Kubuntu onto my Ubuntu system to explore KDE. I noticed, however, the KDE font settings seem to override my gnome settings, even in gnome. I've set up a fairly complex .font.conf file, but these settings seem to be overridden with by KDE. 

What's (almost-not-a-noob-anymore) noob to do? :rolleyes: 

Thanks! :)

---

### Post by darthsabbath on 2006-04-23
Hey, dunno if you've found a solution to this problem, but if not, I hope this will help.  I had the exact same problem, couldn't get anything to work until I renamed the ~/.gtkrc-2.0 file.  If you open this file, it reads...

```

# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Human/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="Sans Serif 11"
}
widget_class "*" style "user-font"

gtk-theme-name="Human"
gtk-font-name="Sans Serif 11"

```

Rename it to something like gtkrc-2.0.bak or something similar, and it should reset your tont settings. 

HTH

Phil

---

### Post by Burgresso on 2006-04-27
Phil:

I haven't found a solution yet. Thank you for your reply; I'll give it a go as soon as I can. I appreciate it.

Burgresso

---

### Post by nickdiacre on 2008-06-19
Hi,

A long time in the past, I know, but I have a similar problem whereby KDE font settings interfere with font settings in the Appearance app in gnome. This includes font sizing and smoothing. Particularly, I cannot change the font/size of the "main_menu" applet in the gnome panel.

Is there a way of sorting this, and allowing one to override the other?

Is it possible to run KDE apps without installing KDE font control?

Thanks if anyone can help....

Regards

The Dog

---

