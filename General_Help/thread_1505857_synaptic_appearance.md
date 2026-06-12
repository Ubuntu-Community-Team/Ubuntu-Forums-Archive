---
title: "synaptic appearance"
date: 2010-06-09
forum: General Help
---

### Post by Crempel on 2010-06-09
A few weeks ago I mentioned that synaptic looks shocking under KDE. I had some friendly replies but couldn't solve the problem. I have now discovered something even stranger: When starting Synaptic on a freshly installed Kubuntu without root privileges it looks like a genuine qt 4 application. Beautiful, but, off course, you cannot install anything. Launching Synaptic as root it looks ugly like gtk 1 again. How can this happen? Apart from the gtk/gnome dependencies that Synaptic needed when I installed it, my system now is pure Kubuntu. Does anyone have a clue? Thanks in advance.:confused:

---

### Post by warfacegod on 2010-06-09
I don't know if Ubuntu Tweak works in Kubuntu or not but it has an option called "Fix Appearance When Root" or something like that. Might be worth a look.

---

### Post by Crempel on 2010-06-10
Thank you warfacegod, I could install Ubuntu Tweaks, but the feature mentioned (or anything similar) is unfortunately not available under Kubuntu. I appreciate your suggestion, though.

---

### Post by Zorael on 2010-06-11
As you know, by using System Settings as your own user, you can set your GTK applications up (via GTK+ Appearance in the Appearance section) to use the QtCurve widget style, making them assume an Qt4-ish look. But the setting is only set for your user and doesn't apply to root.

One thing you can do is to open up System Settings as root and clone your settings, particularly ones relating to appearance (including GTK+ Appearance). '**kdesudo systemsettings**' in a run box (Alt+F2) or a terminal.

You can also make symbolic links in the home directory of root, to make it use your user's setting. The files touched are **~/.kde/share/config/kdeglobals** and **~/.gtkrc-2.0-kde4**.
```
$ sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0-kde4
$ sudo rm /root/.kde/share/config/kdeglobals
$ sudo ln -s ~/.kde/share/config/kdeglobals /root/.kde/share/config/kdeglobals
```

The second solution makes root always follow your user's settings, which can be a good or a bad thing. If you use this approach, then even programs started as root will be updated to use new themes and colors if you change them. If you use the first approach, you'd have to manually make sure the new settings match.

---

