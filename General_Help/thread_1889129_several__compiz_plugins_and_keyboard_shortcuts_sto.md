---
title: "several  compiz plugins and keyboard shortcuts stopped working -- help please!!"
date: 2011-11-30
forum: General Help
---

### Post by blackbird34 on 2011-11-30
(Ubuntu 11.04 Gnome Classic)

Hi
After tweaking around my Buntu i came out with a rather nice customized system, i could do everything with the keyboard (Synapse, Gnome Terminal keyboard shortcut.). I also had a couple of nice (irrelevant) compiz plugins enabled, and the Wobbly Windows plugin, which meant I could snap windows into being exactly half the screen by dragging the moouse cursor over to touch the edge of the screen. 

Yesterday i tried to enable the Desktop Cube (i know it conflicts, i tried before)... It failed and removed all my title bars, but i managed to get everything back except the ability to snap windows (neither the snapping windows nor the wobbly windows work for that) and keyboard shortcuts like ALT+TAB, CTRL+space (synapse search) and CTRL+ALT+T (gnome terminal). However, CTRL+ALT+F1 works for a tty... 

I'm puzzled. Any ideas? :confused:

---

### Post by bluexrider on 2011-11-30
Alt+F2 gconf-editor

apps>compiz>plug-ins

check those settings you feel that are or have issues

if you feel that you want to start over and go back to default settings 

then

Open the terminal and run the following command [INDENT]gconftool-2 --recursive-unset /apps/compiz






[/INDENT]

---

### Post by blackbird34 on 2011-12-01
Ok. that made a nice little mess. 
I rebooted and got Compiz back to normal. Thanks for the tip. Ctrl+Alt+T works too :)

One of my keyboard shortcuts still doesn't work though. 
When i try to reset the Synapse search shortcut, in its preferences, i get a message "Failed to register hotkey 'activate' with signature '<Control>space' ". No idea what it means. 
Control+Space does work to turn it off though.

EDIT: purged and reinstalled synapse, changed to a different keyboard shortcut, everything resolved. Thanks!!

---

### Post by bluexrider on 2011-12-01
Glad to help,

happy *buntu

---

