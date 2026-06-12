---
title: "Desktop Icons Moving Plus..."
date: 2012-04-05
forum: General Help
---

### Post by oaxacamatt1 on 2012-04-05
Hi all,
Has anyone noticed that on Xubuntu 11.10 that the desktop icons move ALL AROUND.  Everytime I log in I find my icons re-arranged with no specific pattern.  Home will not stay on top left for example. Is there a way to make them stationary?  It bugs the heck out of me. 

Also I have noticed that I cannot 'lasso' more than one desktop icon at a time and move them.  In other words, If I box off two or more icons and try to move them (to another location or folder) in unison only one will move.  The rest will not move. Irratating

---

### Post by brainwash on 2012-04-05
[QUOTE=oaxacamatt1]Everytime I log in I find my icons re-arranged with no  specific pattern.[/QUOTE]

Does your screen resolution get changed at some point?

Saving the layout file located in
```
~/.config/xfce4/desktop/
```
before logout and restoring it afterwards might be a solution.

[QUOTE=oaxacamatt1]Also I have noticed that I cannot 'lasso' more than one desktop icon at a time and move them.[/QUOTE]

Yeah, the XFCE desktop manager is pretty limited. Moving more than 1 desktop icon at the same time simply does not work.

---

