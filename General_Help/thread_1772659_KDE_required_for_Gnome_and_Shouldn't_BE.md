---
title: "KDE required for Gnome and Shouldn't BE"
date: 2011-05-31
forum: General Help
---

### Post by jamesisin on 2011-05-31
When I try to launch Software Sources from Gnome-do or via its icon (under System) I get a KDE error dialog:

```
Need administrative powers - Software Sources

Please run this software with administrative rights.  To do so, run this program with kdesudo.
```

Normally when this happens I would just reboot and I could get back to business.  Now on this particular lappy (10.04 32bit) I'm stuck opening Synaptic and spawning Sources from there.

Did I mention this is a Gnome desktop?

Any ideas?

---

### Post by silex89 on 2011-05-31
Wooow :S...

That's weird... I have no idea... :|

I have both KDE and GNOME desktops and when I run something in one desktop that depends of the other, I have no problems......

---

### Post by jerrrys on 2011-05-31
gnome-do can also work in kde by changing some settings.  any chance these settings have been altered on yours?

---

### Post by jamesisin on 2011-05-31
I don't think it's Gnome-do related since the same thing happens using the icon under System.

Digging deeper I notice that the command for the short-cut under System is as follows:

```
software-properties-kde
```

This is totally wrong.  It should be thus:

```
gksu --desktop /usr/share/applications/software-properties-gtk
```

(This according to a different and working 10.04 machine on my network.)

Now what changed that?  I suppose it's something I installed (through Synaptic) or some update, but that's just a guess.  I certainly didn't change it manually.  I'm not clear if Gnome-do is calling the same command or if there is some other redirect occurring.

Is that more helpful?

---

### Post by jerrrys on 2011-05-31
what if you just change that kde to gtk and see what happens

---

### Post by jamesisin on 2011-06-01
I get the "Run program" dialog.  I'll double-check the command I posted above tomorrow (or you can probably confirm it on your system) in case I typed it incorrectly.

---

### Post by jamesisin on 2011-06-01
Yep.  I missed much of the command when I typed it into this window while looking at that machine.  Here's the correct (full) command:

```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
```

This does allow the shortcut to work.  Of course I did this change test on a shortcut I created on the Desktop.  I'm not clear how to get to the Properties dialog for a shortcut located in the menus (since that is not a right-click option in those menus).

Also I'm not sure as yet if fixing the shortcut will also fix the Gnome-do problem.

---

### Post by jamesisin on 2011-06-01
Ok, I found the Properties dialog through the Menu Editor.  That allowed me to fix the shortcut under System.

This does NOT unfortunately fix Gnome-do.

Suggestions?

---

### Post by jamesisin on 2011-06-04
Anyone have an idea for fixing the Gnome-do problem?

---

