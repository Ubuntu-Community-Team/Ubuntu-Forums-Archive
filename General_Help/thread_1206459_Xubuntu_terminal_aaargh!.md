---
title: "Xubuntu terminal aaargh!"
date: 2009-07-07
forum: General Help
---

### Post by cd-r80 on 2009-07-07
I cannot make GUI launcher because of crashing terminal. I put xterm as ubuntu default which does not crash. But XFCE seems still use other terminal when using panel button and logs me out. How to stop and change how my button opens terminal? I need my button to open terminal for asking paswword.

I don't want to lower color depth ( cause of crashing XFCE terminall...).

---

### Post by kerry_s on 2009-07-07
you must have a intel vid card. 

to set xterm as default, select "X Terminal" in the prefered applications.
for the button, right click> properties, then change the command
but you shouldn't have to change the launcher if you set xterm as default.

---

### Post by cd-r80 on 2009-07-07
Ok thanks. I also found other solution:

xorg.conf:

Section "Extensions"
Option "Composite" "Disable"
EndSection

---

### Post by kerry_s on 2009-07-07
> **cd-r80 said:**
> Ok thanks. I also found other solution:

xorg.conf:

Section "Extensions"
Option "Composite" "Disable"
EndSection

yep, thats the intel fix.

---

