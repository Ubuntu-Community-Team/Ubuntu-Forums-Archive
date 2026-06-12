---
title: "execute command without login"
date: 2010-09-14
forum: General Help
---

### Post by waliu on 2010-09-14
Hello,

here is my question: I want to start my Ubuntu 10.04 and without logging in I need a command started. The command is setxkbmap ....

So, I will not put the command in my .profile, nor in my .bashrc, because I am not going to login.

Any suggestions?
Thanks!

---

### Post by dcstar on 2010-09-15
> **waliu said:**
> Hello,

here is my question: I want to start my Ubuntu 10.04 and without logging in I need a command started. The command is setxkbmap ....

So, I will not put the command in my .profile, nor in my .bashrc, because I am not going to login.

Any suggestions?
Thanks!

/etc/rc.local

---

### Post by rnerwein on 2010-09-15
hi
it's the matter what you want to do. if you want to run the command only once --> you can use the /etc/rc.local.
if you want to run the command perodicly you can use the "crontab- see man crontab 5 ". ( e.g. every 10 minutes, 10 hours, once a day or so on)
ciao

---

