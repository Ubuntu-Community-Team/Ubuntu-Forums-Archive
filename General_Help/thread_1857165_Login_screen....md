---
title: "Login screen..."
date: 2011-10-09
forum: General Help
---

### Post by Opar on 2011-10-09
My ubuntu stopped loging into my Default account.. just wouldn't do it when it started up.... So I started it in safe mode fixed it all up so autologin was off made a new account with a new home dir and i can't login to that one either it just brings me back to the login screen like nothing happened... anyone know how to fix this?

---

### Post by hollowsyndicate on 2011-10-09
which ubuntu you using?

---

### Post by Opar on 2011-10-09
11.04

---

### Post by hollowsyndicate on 2011-10-09
did u upgrade the graphics drivers?

---

### Post by Opar on 2011-10-09
I don't have a graphics card :mad:

---

### Post by hollowsyndicate on 2011-10-09
wat kinda pc are u using?

---

### Post by Opar on 2011-10-09
Old gateway 506gr Small amount of ram 200gb hhd p4 pretty bad computer :/

---

### Post by hollowsyndicate on 2011-10-09
type this in terminal 

lspci -nn | grep VGA

put wat it says in ur post.

---

### Post by Opar on 2011-10-09
VGA compatible controller [0300]: Intel corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)

---

### Post by hollowsyndicate on 2011-10-09
lol intel. did you update before it started to log u out?

---

### Post by Opar on 2011-10-09
No i didn't.

---

### Post by hollowsyndicate on 2011-10-09
do u know how 2 use ctrl+alt+f1 to login?

---

### Post by Opar on 2011-10-09
yeah... Ik how to login through the terminal shells or w/e

---

### Post by hollowsyndicate on 2011-10-09
> **Opar said:**
> yeah... Ik how to login through the terminal shells or w/e

k. login type 

sudo service gdm stop 

startx

---

### Post by Opar on 2011-10-09
Works but... There are no menu's on the top and bottom
Works Nvm, Do i have to do this every time?

---

### Post by hollowsyndicate on 2011-10-09
unity -,-

on the login screen make the session thing ubuntu classic or watever it is on 11.04, and try to login, then do that stop gdm startx thing again.

---

### Post by Opar on 2011-10-09
Thanks! Works perfectly now :guitar:
i was about to stab my computer.

---

### Post by hollowsyndicate on 2011-10-09
lol kk xd.

---

### Post by Opar on 2011-10-09
I <3 10.04 lts ...... But...... Downgrading means i have to re-install all my packages for coding and sdk's for android app making and transfer all my Source and shiz to 10.04....
After i upgraded i wanted to go back but...

---

