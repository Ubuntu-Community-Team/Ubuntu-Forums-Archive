---
title: "startup"
date: 2010-03-14
forum: General Help
---

### Post by joshbrice on 2010-03-14
Can you make it so that its is a command line at startup insted of going straight to the gui login???

---

### Post by l4zy on 2010-03-15
This will remove X start on boot

sudo update-rc.d -f gdm remove 

if u have KDE replace gdm with kdm

---

