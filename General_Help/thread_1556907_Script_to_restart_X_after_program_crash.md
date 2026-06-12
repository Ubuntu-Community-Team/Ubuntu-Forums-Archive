---
title: "Script to restart X after program crash"
date: 2010-08-20
forum: General Help
---

### Post by speed32219 on 2010-08-20
What I would like to do is if the app crashes which kills xinit for the system to either kill login (which will auto login and restart the app) or just to execute the startx command (which auto launches the app) as if typed in from the keyboard. I am trying to find a way that will use the least amount of system resources, rather than a loop.

I've searched but most everything I find is for an autostart which I already have working from a fresh power up.

Thank you

---

### Post by regala on 2010-08-20
> **speed32219 said:**
> What I would like to do is if the app crashes which kills xinit for the system to either kill login (which will auto login and restart the app) or just to execute the startx command (which auto launches the app) as if typed in from the keyboard. I am trying to find a way that will use the least amount of system resources, rather than a loop.

I've searched but most everything I find is for an autostart which I already have working from a fresh power up.

Thank you

which program crash ? why trying to do what the login manager will do for you ?
could you explain precisely what's happening and what you would want it to do ?
seems like you are trying to reinvent the wheel here. configure gdm to use autologin.

---

