---
title: "Screensaver commands from terminal window"
date: 2011-06-23
forum: General Help
---

### Post by william_ia on 2011-06-23
Hi All,

We have created a stripped own version of Ubuntu 10.04 LTS, and removed the screen saver and power management options from the desktop as we have turned off the menu. The reason for this is security as we do not want users having any other options then what shows on the desktop. 

What is the sudo command to get back to this or do I need to under the administrator profile Create a Launcher icon?

---

### Post by william_ia on 2011-06-23
Found the answer with a little more research on my part.

We have another machine with full blown Ubuntu 10.04 still installed on  it. Went to the menu and found that all I had to do was create a  launcher icon of:

Screen Saver
gnome-screensaver-prefernces

then run that when the icon becomes active and continue from there.
Hopefully this will help someone else.

---

