---
title: "Help! Can't Login - Keep returning to login screen!"
date: 2010-06-02
forum: General Help
---

### Post by Gremlyn1 on 2010-06-02
I was messing with Mount Manager, trying to get my normal user to have write permissions to a samba share, and decided to try logging out and back in to see if my changes worked. After logging out, I can't log back in! The login screen comes up, but after entering my password I just get kicked back to the login screen.

Background on the machine: This is Lucid running with the latest updates, it is a guest OS in vbox, which is running in Windows. It's the latest version of vbox, 3.18.xxxxxxx or whatever it is.

I have attached my xsession-errors and Xorg.0.log, hopefully they are helpful to someone. This is my work machine and I do the majority of my work on here! :(

---

### Post by Gremlyn1 on 2010-06-02
I found this bug: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/539440?comments=all](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/539440?comments=all)
This does not appear to be my issue. I'm not seeing anything odd in my syslog.

---

### Post by dino99 on 2010-06-02
try: sudo service gdm stop

---

### Post by Gremlyn1 on 2010-06-02
I actually just tried stopping it, and then ran startx. It is running, though it's using software rendering to display because vbox doesn't support something or other. I'm assuming  I am waiting for it to load up, it's just a blank screen right now. It's probably taking a little longer because I'm also dumping out all important files to my windows host OS in case I can't recover the Ubuntu guest. Going to go to lunch and see where it's at when I return.

---

### Post by Gremlyn1 on 2010-06-02
No luck with the startx. I got to a blank screen, and though I couple of KDE based notifications came up, I have a blank screen still.

---

### Post by Gremlyn1 on 2010-06-02
OK, now I've really done it! I uninstalled gdm, ran clean, then reinstalled and only get a white terminal box in the top left of the screen at login. Going to try to repair from the LiveCD.

---

### Post by Gremlyn1 on 2010-06-02
I may be talking to myself here, but I have fixed it! When I reinstalled gdm, it didn't put gnome-panel back, so after manually installing it (apt-get install gnome-panel), everything is as it should be.

---

### Post by Jeroensum on 2010-06-03
Hey, good for you!
Learning linux by breaking & fixing things is the way most people do so this will probably be your first fix in a row of many ;-)

Btw, plz mark your post as [SOLVED]  so everyone knows it's been fixed, heck even put [SOLVED IT MYSELF AND PROUD OF IT!]  if you want ;-)

---

### Post by Gremlyn1 on 2010-06-03
> **Jeroensum said:**
> Hey, good for you!
Learning linux by breaking & fixing things is the way most people do so this will probably be your first fix in a row of many ;-)

Btw, plz mark your post as [SOLVED]  so everyone knows it's been fixed, heck even put [SOLVED IT MYSELF AND PROUD OF IT!]  if you want ;-)

I looked to see if I could change the prefix, but it was available as an option. I take I just type the [Solved] part myself then?

---

### Post by Jeroensum on 2010-06-06
Yup, that's all manual labour here ;-)

---

### Post by llawwehttam on 2010-06-06
You just press           thread tools> Mark as solved         at the top.

---

