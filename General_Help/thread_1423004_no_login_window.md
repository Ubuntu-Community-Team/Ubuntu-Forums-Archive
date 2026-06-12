---
title: "no login window"
date: 2010-03-06
forum: General Help
---

### Post by permant on 2010-03-06
Hi all:
karmic goes well until last update , login window does not show after boot up , so I try ctrl+alt+f1 ,and input name and password, then startx ,but get some fetal err :Invalid MIT-MAGIC-COOKIE-1 key ...bla bla bla
when I try alt+f7 ,the login window appears! input name and password ,goes well again ,so every time ,I have to try more steps to login ubuntu, 
any suggestion?
thanks!

---

### Post by Intrepid Ibex on 2010-03-06
Some setting error. The login window will always be found in tty7 with Ubuntu.

So when you execute startx/xinit, X (your login window) will start on that tty(7). But it is supposed to get there automatically. Did you try "sudo dpkg-reconfigure gdm" and selecting gdm from there to have it open up by default?

---

