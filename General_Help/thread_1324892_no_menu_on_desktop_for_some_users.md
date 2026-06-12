---
title: "no menu on desktop for some users"
date: 2009-11-12
forum: General Help
---

### Post by nagaraj on 2009-11-12
after upgrading from 8.04 to 9.04 i started having this prolem. the desktop of some users is not showing the main menu bar at all. the screen just looks like this - 
[IMG]file:///home/manulodaya1/Desktop[/IMG]

how do i correct this?[ATTACH]135998[/ATTACH]

---

### Post by fluffman86 on 2009-11-12
1. Try pressing alt+f2 and run "nautilus" just to see what happens.  It should be running already, though, since you have a folder there.
2. alt+f2 again, this time do "gnome-panel"
3. if you still get nothing, alt+f2, "gnome-terminal" and do the following commands from there.

Let us know what happens.

---

### Post by fluffman86 on 2009-11-12
Also, take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1324881](http://ubuntuforums.org/showthread.php?t=1324881)

It may help you figure out how to add a panel there.

---

### Post by nagaraj on 2009-11-13
thanks, this is what happened
alt+f2 did not do anything. opened filesystem>usr>share>applications>terminal and ran 'nautilus'. it returned
_(nautilus:2640): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed_
and opened home folder in file browser.

then i ran 'gnome-panel' - it returned
[U]manulodaya@DUTY-ROOM-DESKTOP:~$ gnome-panel
** (gnome-panel:2606): DEBUG: Adding applet 0.
** (gnome-panel:2606): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2606): DEBUG: Adding applet 1.
** (gnome-panel:2606): DEBUG: Adding applet 2.
** (gnome-panel:2606): DEBUG: Adding applet 3.
** (gnome-panel:2606): DEBUG: Adding applet 4.
** (gnome-panel:2606): DEBUG: Adding applet 5.
** (gnome-panel:2606): DEBUG: Adding applet 6.
** (gnome-panel:2606): DEBUG: Adding applet 7.
** (gnome-panel:2606): DEBUG: Adding applet 8.
** (gnome-panel:2606): DEBUG: Adding applet 9.
** (gnome-panel:2606): DEBUG: Adding applet 10.
** (gnome-panel:2606): DEBUG: Adding applet 11.[/U]

it is stopping at applet11 and not completting the process. but i can see the main panel and menu have appeared. i am waiting. should i just go ahead and close the terminal? or wait for the process to complete?

---

### Post by nagaraj on 2009-11-13
just found out that the following were unchecked in 'startup applications preferences'
[LIST=1]
[*]UME Desktop Launcher
[*]UNR Launcher
[/LIST]
do they have anything to dpo with this? i have anyway checked those two now.

---

### Post by nagaraj on 2009-11-13
but the terminal is stuck there!!

---

### Post by nagaraj on 2009-11-13
solved - i just restarted with terminal still hanging at that point. on rebooting the panel was there alright.
thanks fluffman86.

---

