---
title: "Shutdown menu's disappeared"
date: 2010-12-15
forum: General Help
---

### Post by Zeophlite on 2010-12-15
I think this occurred after I used Update Manager, but the shutdown menu up the top right has disappeared!  In its place is my name (like a repeat from the chat menu).

[IMG]http://img535.imageshack.us/img535/9498/screenshotzi.png[/IMG]

I know I can restart with:
sudo shutdown -r now
But why has this error occurred?

Thanks

---

### Post by Hippytaff on 2010-12-15
its happened to me too, but it's always fixed it's self after rebooting so haven't bothered looking into it

---

### Post by Crusty Old Fart on 2010-12-15
If it stays hosed after reboot, you might try this:

[LIST]
[*]Right click on the shutdown menu and select: Remove From Panel
(It almost looks like your shutdown menu is in there more than once and
 doing some weird kind of overlap. So, you may need to repeat this step
 until you get a vacant space on the panel where the shutdown menu used to
 reside -- just a guess, who knows?)
[*]Right click in the vacant space on the panel and select: Add to Panel...
[*]From the Add to Panel window, select: Indicator Applet Session
[*]Click on the Add button, then on the Close button
[/LIST]
Good Luck.

---

### Post by NCLI on 2010-12-15
If this ever happens again, just press alt+F2, then enter this command:
```
gnome-panel --replace
```
This bug will be fixed in Ubuntu 11.04, due to the deprecation of gnome-panel.

---

### Post by Hippytaff on 2010-12-15
> **NCLI said:**
> If this ever happens again, just press alt+F2, then enter this command:
```
gnome-panel --replace
```
This bug will be fixed in Ubuntu 11.04, due to the deprecation of gnome-panel.
 
Excellent :-)

---

### Post by prasopsuk on 2011-04-03
> **NCLI said:**
> If this ever happens again, just press alt+F2, then enter this command:
```
gnome-panel --replace
```
This bug will be fixed in Ubuntu 11.04, due to the deprecation of gnome-panel.
Thank you.

---

