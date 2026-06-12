---
title: "Lost Icon"
date: 2010-03-13
forum: General Help
---

### Post by ronc69 on 2010-03-13
I have ubuntu 8.04 and am trying tp update to 9.1. In the course of investigating I have inadvertently deleted the icon (bottom left of screen) which leads to my systems menus. Can anyone advise me how to get it back as I have lost access to me system functions.

---

### Post by ronc69 on 2010-03-13
I have ubuntu 8.04 and am trying tp update to 9.1. In the course of investigating I have inadvertently deleted the icon (bottom left of screen) which leads to my systems menus. Can anyone advise me how to get it back as I have lost access to my system functions.

---

### Post by hvbakel on 2010-03-13
Right-click the taskbar, select "add to panel" and then select the "Main menu" applet.

---

### Post by n0dix on 2010-03-13
Why do you open a new thread with the same problem?
[http://ubuntuforums.org/showthread.php?t=1429301]("http://ubuntuforums.org/showthread.php?t=1429301")

---

### Post by howefield on 2010-03-13
> **n0dix said:**
> Why do you open a new thread with the same problem?
[http://ubuntuforums.org/showthread.php?t=1429301]("http://ubuntuforums.org/showthread.php?t=1429301")

The posts were posted almost simultaneously, a few seconds apart by the looks of it as I'm sure you are aware, most likely a mistake. 

Why don't you just report the duplicate ?

---

### Post by dcstar on 2010-03-13
> **ronc69 said:**
> I have ubuntu 8.04 and am trying tp update to 9.1. In the course of investigating I have inadvertently deleted the icon (bottom left of screen) which leads to my systems menus. Can anyone advise me how to get it back as I have lost access to my system functions.

Right-click the panel and add it back in.

---

### Post by Villiam on 2010-03-13
You have to manually start a program by open the Configuration Editor, by running the program gconf-editor
Choose apps->nautilus->desktop
Tick the box beside computer_icon_visible, home_icon_visible, and trash_icon_visible (or any of these as per your requirement). The changes take effect immediately.

---

### Post by lidex on 2010-03-14
> **Villiam said:**
> You have to manually start a program by open the Configuration Editor, by running the program gconf-editor
Choose apps->nautilus->desktop
Tick the box beside computer_icon_visible, home_icon_visible, and trash_icon_visible (or any of these as per your requirement). The changes take effect immediately.
That will put those icons on your desktop - for those who like the windows look ;)

---

