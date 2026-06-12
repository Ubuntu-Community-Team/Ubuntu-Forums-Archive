---
title: "Authentication (password) window shakes and won't let me enter a password"
date: 2010-04-28
forum: General Help
---

### Post by ram2500 on 2010-04-28
I have a rather difficult problem. Every time I need root privileges and I am asked to authenticate (i.e. Update Manager, mounting a partition, etc), the password window comes up, shakes and immediately closes, leaving me with no chance to enter a password. What to do?

edit: this is NOT the login window, just the little dialog that pops up when you need elevated privileges.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
In a command line type ```
gksudo gedit
``` and see what it spews out on the command line when you try to enter your password. Post here if you don't now what to do from there.

---

### Post by ram2500 on 2010-04-28
It allows me to enter my password and lets me into gedit, but the problem lies with trying to mount a partition, install a program via Software Center (tried this just to verify) and other special-privileged actions. What's going on?

---

### Post by sisco311 on 2010-04-28
What happens when you run:
```
pkexec echo 1
```
?

Is your user in the admin group?
```
id
```

---

### Post by ram2500 on 2010-04-28
Running pkexec echo 1 pops up a password dialog, shakes and closes. 

I am in the admin group according to "id" and should be as this is my laptop:). 

This is really strange behavior, and only happened after an update, I suppose.

---

### Post by ram2500 on 2010-04-29
I am also apart of three other forums (AtoZ Teacher Stuff, RV Forums, and Mopar Forums), and I've noticed that when posts get "buried" on top of new ones, people repost (bumping?)--- Is it acceptable to "bump" in Ubuntu Forums? (This is a critical problem for me, how the password dialogs aren't working.) 

ANY help would be much appreciated. In case you don't read previous posts (although HIGHLY encouraged), my problem is that the ***_password dialog that comes up when you need special privileges shakes and immediately closes_***, giving me NO chance to enter a password.

---

