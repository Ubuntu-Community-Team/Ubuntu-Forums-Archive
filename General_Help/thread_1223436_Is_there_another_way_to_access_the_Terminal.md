---
title: "Is there another way to access the Terminal?"
date: 2009-07-26
forum: General Help
---

### Post by AmericanPrincess109 on 2009-07-26
I don't know how, but I changed something on my computer and now I can't find the terminal. It's not under Accessories anymore.
is there another way to find the terminal?

---

### Post by Gen2ly on 2009-07-26
Well you could do Ctl + Alt + F1 and get to a console.  Oh wait ... oy!  Do Alt + F2 and type in gnome-terminal should do the trick.  Re-installing should give you your desktop icon back.

---

### Post by AmericanPrincess109 on 2009-07-26
Thank you so much!!

---

### Post by chandru on 2009-07-26
You can also edit the menus.

Right click on the ubuntu application icon in the top left and choose edit menus.

Click Accessories (under Applications). If there is an entry for terminal already, just click in the box next to it. Otherwise, click the "New Item" button. In the window that appears, use the following options

Type: Application
Name: Terminal
Command: gnome-terminal
comment: Use the command line

This should restore the menu entry.

---

