---
title: "Command line to uninstall PopTray Minus"
date: 2010-01-27
forum: General Help
---

### Post by chisle on 2010-01-27
I installed it to see if i could get it working, but after reading and realizing ymail accounts need to be paid for in order to access the pop3 server i was dissappointed in not being able to connect to my mail without the browser. well anyway i am a fairly new user, started using ubuntu and linux in general in september and therefore i rely heavily on GUI so don't know to much about the terminal. anyway Poptray minus doesnt show up in any of the GUI managers for removing or installing packages so i was hoping someone could give me the command line for the terminal to unistall this application. much thanks and appreciation.

---

### Post by Leppie on 2010-01-27
how did you install it?

you can access ymail using thunderbird and the webmail plugin: [http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by chisle on 2010-01-27
i installed it using the .deb package installer

---

### Post by Leppie on 2010-01-27
then you should be able to find it like this:
```
dpkg -l | grep poptray
```

---

### Post by lenik on 2010-01-27
> **chisle said:**
> i installed it using the .deb package installer

you should be able to uninstall it using:

sudo apt-get remove poptrayminus

---

### Post by chisle on 2010-01-28
thanks, done. where would i be able to read in order to understand basic command lines? once again thanks

---

### Post by lenik on 2010-01-28
> **chisle said:**
> thanks, done. where would i be able to read in order to understand basic command lines? once again thanks
any beginner book about ubuntu will do, me thinks.
however, cannot recommend any particular title, sorry.

---

### Post by Leppie on 2010-01-28
pages like this: [http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

---

