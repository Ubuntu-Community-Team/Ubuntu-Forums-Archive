---
title: "Can't run gui applications as root"
date: 2009-07-10
forum: General Help
---

### Post by peterdm on 2009-07-10
Hi,

Since Jaunty, I can't run gui applications as root anymore. Using glxgears as a simple example app, I am logged in as myself, I open a console and I do the following:

```

peter@cheetah:~$ sudo su -
root@cheetah:~# glxgears 
Error: couldn't open display (null)

```

This definitely worked in the past (Intrepid?).
Any ideas how to properly fix this?

Thanks,

Peter

---

### Post by Regenweald on 2009-07-10
try using gksudo instead. It's really meant for GUI apps.

---

### Post by LightningCrash on 2009-07-10
Do sudo -s instead of sudo su -

In addition, su - does a complete login, resets your X environment variables (like DISPLAY), so the program won't know which X screen to talk to.

$ env|grep DISPLAY
DISPLAY=:0.0
$ sudo -s
# env|grep DISPLAY
DISPLAY=:0.0
# exit
$ sudo su -
# env|grep DISPLAY
(there was no output)
# exit
$ sudo su
# env|grep DISPLAY
DISPLAY=:0.0
# exit


the su - will break X apps every time.

---

