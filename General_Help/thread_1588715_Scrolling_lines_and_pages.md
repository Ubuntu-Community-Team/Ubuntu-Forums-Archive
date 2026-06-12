---
title: "Scrolling lines and pages"
date: 2010-10-05
forum: General Help
---

### Post by dkjMusic on 2010-10-05
I pursued how to mouse-wheel scroll pages in Ubuntu for several days in various forums to no avail. Then I noticed the Advanced Settings for Firefox 3.6 which lets you do exactly what I wanted: normal scroll by lines (number specified or use system default) **and** CTRL-scroll by pages. Of course, this only applies to Firefox scrolling and not to, e.g., scrolling Nautilus windows.

My questions: Can the same be done in Ubuntu? If not, how can this feature be suggested for inclusion?

---

### Post by dkjMusic on 2010-10-08
Accomplished what I wanted with the following steps:

1. Create copies of the original imwheelrc and startup.conf as backups in the /etc/X11/imwheel folder (after chown'ing to me for the folder and its contents). 

2. Edit startup.conf to change IMWHEEL_START=0 to IMWHEEL_START=1.

3. Edit imwheelrc to add the following lines:
".*"
None,           Up,     Up
None,           Down,   Down
Control_L,      Up,     Page_Up
Control_L,      Down,   Page_Down

4. Restart the computer to activate the changes to imwheelrc and startup.conf .

Each window now scrolls by lines by rolling the mouse wheel up or down and scrolls by pages by pressing the left CTRL button while rolling the mouse wheel up or down.

---

