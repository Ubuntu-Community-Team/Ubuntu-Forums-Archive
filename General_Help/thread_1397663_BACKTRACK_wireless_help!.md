---
title: "BACKTRACK wireless help!"
date: 2010-02-03
forum: General Help
---

### Post by phoenixfire900 on 2010-02-03
I need help i cant connect to the internet with backtrack can anyone help me set up my wireless card so i can connect? thanks

---

### Post by diablo69er on 2010-02-03
Might I suggest using backtrack forums and or Google?

To save you some trouble try this

sudo -s
/etc/init.d/wicd start
su user
startx

make sure that's done right after you login before starting the GUI.  

Hope that helped

---

### Post by phoenixfire900 on 2010-02-03
i tried and it didnt work none of my wireless networks show and my IP address is stuck on loopback.  How do I manually change my IP address?

---

