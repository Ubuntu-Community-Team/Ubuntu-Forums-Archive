---
title: "mouse loses click ability"
date: 2010-02-16
forum: General Help
---

### Post by strattonbrazil on 2010-02-16
Yesterday I came to my computer and the left mouse click was no longer working.  The mouse could still move the curser, scroll with the scroll wheel, and right click brought up popup menus as usual.  However, the left click just didn't work.  

I thought my optical mouse had finally kicked the bucket, but it felt fine inspecting it.  I reset my computer, which didn't make a difference, and even tried swapping out mice.  With both mice, however, the left button didn't work.  I even tried deleting .gnome and .gconf, but that didn't seem to affect the mouse.  I also turned desktop effects completely off.  

I finally got Firefox open (since some menus work with right-click) and found some people had success left-clicking via Ctrl-shift.  I started trying all sorts of key combinations with Ctrl, shift, alt, and super.  Finally after all the attempts, including me losing right-click and scrolling, I finally got everything working leading me to believe it was some state I got into and out of via a keystroke.  However, a person on my computer at home now says the problem is back.  It worked fine up until yesterday and I don't believe we upgraded anything.  

Is someone familiar with this problem or know how to fix it?  Both mice I tried were USB if that matters.  I'm running Ubuntu 9.10.

---

### Post by undecim on 2010-02-16
Go to a terminal and type "dmesg | tail" and post the output here, please.

EDIT: Also, for working without a mouse, here are some shortcuts you can use until this is resolved:

Alt+F1: Open the main menu (use arrow keys to navigate)
Alt+F2: Start a program by name (press alt+f2 and type "gnome-terminal" for a terminal)
Alt+Tab: Switch between open windows
Alt+F4: Close a window
Alt+X: Select object from the current window with "x" underlined. For example, "Alt+F" in Firefox opens the file menu. From there, you can use arrow keys to navigate, and even move to the adjacent menus.

---

