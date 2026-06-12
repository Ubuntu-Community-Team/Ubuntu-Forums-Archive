---
title: "Launcher Program Malfunction"
date: 2012-06-04
forum: General Help
---

### Post by WBMachinery on 2012-06-04
I recently installed Maple 13 (without any predetermined installer) on the root folder, yet I can't seem to get the icon of the program to lock to the launcher, when I do, all I see is an icon of Java that has no function. 

I've tried changing its permission via properties but no dice, I've even tried pasting a shortcut to the desktop but it has no effect. It only runs when I open it from nautilus with root privileges.


Any help is appreciated.

---

### Post by Los Frijoles on 2012-06-04
Have you tried adding gksudo to the command that is run when you click the icon?

Example:

/path/to/program
turns into:
gksudo /path/to/program

---

### Post by WBMachinery on 2012-06-04
Sorry I probably wasn't clear with my problem, the program works fine and all, apart from not locking to the launcher it doesn't appear on the dashboard when I search for it, so the only way I can run it is either with that command or going through the directories, all I want to do is for it to appear on the dashboard or on the launcher.

---

### Post by dmouck on 2013-01-22
Did you find a solution to this? I'm facing the same issue (Maple 16 on Ubuntu 12.10 x64). I have copied the maple16.desktop file to /usr/share/applications, but when I run Maple, a Java icon appears instead of Maple.

---

