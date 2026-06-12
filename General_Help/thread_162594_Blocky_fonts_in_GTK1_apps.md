---
title: "Blocky fonts in GTK1 apps"
date: 2006-04-19
forum: General Help
---

### Post by tOz666 on 2006-04-19
Hi, I'm using the Microsoft Core fonts for displaying my apps (Arial, Times New Roman, etc.), I have font antialiasing turned off and the appearance of the fonts of KDE/QT and Gnome/GTK2 apps look pretty well, the fonts render just like they were from Windows, that is, they are thick and display well at almost any size.
I have set up my browsers too and they display the fonts I want.

The problem is that when I try to set up the fonts of the gtk1 apps using gtk-theme-switch, I choose the Arial font, but it doesn't display as well as the gtk2 and qt apps do.

This is a shot of xmms, using arial font, with my current setup:

[IMG]http://telefonica.net/web2/toz/gtk1bad.png[/IMG]

As you can see, the fonts are blocky and aren't as good displayed as these:

[IMG]http://telefonica.net/web2/toz/gtk1good.png[/IMG]

These shot is from a knoppix livecd, using the Helvetica font. Arial is very similar to helvetica, and the font is displayed like the way I want.

Tried to use Helvetica in my kubuntu setup to try to solve the issue, but even helvetica shows blocky too.

I'm thinking to take the /etc/gtk/gtkrc from knoppix and apply it to my setup, but I don't want to break something, so I'm waiting if someone knows a better solution, but if it involves recompiling something, like, gtk1 libraries, it's better to not to mess up things and leave them like they are. ](*,)

---

