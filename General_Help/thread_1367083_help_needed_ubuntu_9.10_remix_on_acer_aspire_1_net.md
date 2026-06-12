---
title: "help needed ubuntu 9.10 remix on acer aspire 1 netbook"
date: 2009-12-29
forum: General Help
---

### Post by draxenth on 2009-12-29
when I unplug my acer aspire one D150 it will go into sleep mode, how do i fix this problem so that I can use it on battery power?

---

### Post by nkleeman on 2010-01-01
I'm running the non-UNR 9.10 on my netbook, Acer Aspire One D250, I have the same issue. Whenever I unplug the netbook it goes into sleep mode.

Found a fix:
[http://ubuntuforums.org/archive/index.php/t-1341435.html](http://ubuntuforums.org/archive/index.php/t-1341435.html)

Read Aearenda fix, works like a charm. I'll post it here.

1. Press ALT and F2 to bring up the 'run command' box.
2. Type 'gconf-editor' (without the quotes) and press ENTER.
3. Find /apps/gnome-power-manager/buttons/ in the tree on the left.
4. Double-click 'lid_ac' in the right pane.
5. Type 'nothing' (without the quotes) into the box that pops up, and press ENTER.
6. Double-click 'lid_battery' in the right pane.
7. Type 'nothing' (without the quotes) into the box that pops up, and press ENTER.
8. Close the editor.

---

