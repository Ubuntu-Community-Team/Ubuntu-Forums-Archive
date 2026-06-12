---
title: "Xorg.conf is empty?"
date: 2006-06-30
forum: General Help
---

### Post by AlexBryan on 2006-06-30
Hi, I had this problem before, but I've formated the hard drive since then, and I'm using a new Ubuntu live CD. When open xorg.conf from Ctrl+Alt+F1 it is blank, the options show on the top and bottom, but there is no text. I need to make a change to this file before I can log in so I can't access the file from Knome. I'm using 'sudo pico etc/X11/xorg.conf' to open the file from the live cd. What is going wrong?

---

### Post by joshrobinson on 2006-06-30
[QUOTE=AlexBryan]Hi, I had this problem before, but I've formated the hard drive since then, and I'm using a new Ubuntu live CD. When open xorg.conf from Ctrl+Alt+F1 it is blank, the options show on the top and bottom, but there is no text. I need to make a change to this file before I can log in so I can't access the file from Knome. I'm using 'sudo pico etc/X11/xorg.conf' to open the file from the live cd. What is going wrong?[/QUOTE]

ive never opened it on the live cd.. but make sure that you didnt capitilize Xorg.conf like you did on your title to this thread :p

X11 should be caps tho

oh yeah.. and put a / in front of etc!!
```
sudo pico /etc/X11/xorg.conf
```

---

