---
title: "Xubuntu terminal cursor blinking"
date: 2012-03-10
forum: General Help
---

### Post by Marzata on 2012-03-10
How to make the Xfce Terminal cursor blinking? 

System: 
Xubuntu 11.10 (oneiric)
Xfce Terminal Emulator 0.4.8

---

### Post by The Cog on 2012-03-10
I prefer gnome-terminal. That blinks: **sudo apt-get install gnome-terminal**. Also, the scroll wheel works while you are looking at man pages in gnome-terminal. I don't know how to make xfce4-terminal blink.

---

### Post by Toz on 2012-03-10
Edit ~/.config/Terminal/terminalrc and change:
> MiscCursorBlinks=FALSE
...to read:
```
MiscCursorBlinks=TRUE
```

---

### Post by Marzata on 2012-03-10
Thank you!

---

