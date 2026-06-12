---
title: "autologin and timedlogin load a black screen"
date: 2009-10-03
forum: General Help
---

### Post by trancegoa on 2009-10-03
Hello I am new to the forums and ubuntu and I'm really lost about what I should do next

I basically followed this miniguide [https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin) to enable **autologin** after a **fresh install** of ubuntu **Jaunty** as I'd be the sole user of my **laptop** but I haven't managed to get it work correctly till now, the only thing I get is a **black background** and my mouse cursor. I have waited up to 10 minutes for the GUI to come up without results and the funny thing is if I do alt+f1 and restart gdm typing 

sudo /etc/init.d/gdm restart

it loads perfectly. 

**TimedLogin** has the same behaviour as AutoLogin but I have to edit /etc/gdm/gdm.conf-custom to disable it if i want to access gnome (since it goes recursive)

By the way, I use** disk encryption**, do you think it has something to do with this? I have tried nearly everything I've come across on this forum and others but any input to solve this issue would be really appreciated

---

### Post by trancegoa on 2009-10-03
it seems it does have to do with encryption

quite simple: encryption (home) and autologin are incompatible

---

### Post by caveman-jim on 2009-10-08
Thanks! I was struggling with this myself.

---

