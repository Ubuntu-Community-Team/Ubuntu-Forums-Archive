---
title: "Runlevel 1 with Upstart in 10.04"
date: 2011-03-17
forum: General Help
---

### Post by FastEddieLB on 2011-03-17
Hi, I'm a new user to Linux in general and I'm trying to get the nVidia drivers installed on Ubuntu 10.04, however I need to disable X Server and after thoroughly searching Google I've found that the best (and, indeed perhaps only) way for me to do this is to get Upstart to boot Ubuntu into runlevel 1. The problem is that I can't find *how* to get Upstart to do this, or maybe I just don't fully understand what some of the more complex things are trying to tell me.

Help is appreciated, a step-by-step guide on using Upstart would be preferable. 

And yes, I'm running as root.

---

### Post by FastEddieLB on 2011-03-17
Bump

---

### Post by ~Plue on 2011-03-17
dunno much about upstart but you could stop X from a virtual console - without switching runlevels
just switch to tty1 run [I]sudo /etc/init.d/gdm stop 

[/I] and also you'll need to blacklist nouveau  before the driver from the nvidia site can be installed. the installer could do that for you but you'll need to restart for the changes to take effect

edit:/ since you said you're new, you might not know this but from within gnome, the
 'system >> administration >> 'additional drivers' or 'Hardware drivers' can download and install the driver for you without much hassle

---

### Post by FastEddieLB on 2011-03-17
> **~Plue said:**
> dunno much about upstart but you could stop X from a virtual console - without switching runlevels
just switch to tty1 run [I]sudo /etc/init.d/gdm stop 

[/I] and also you'll need to blacklist nouveau  before the driver from the nvidia site can be installed. the installer could do that for you but you'll need to restart for the changes to take effect

Already tried all of that, didn't work.

---

### Post by ~Plue on 2011-03-17
> **FastEddieLB said:**
> Already tried all of that, didn't work.
whats the error you're getting then?

(btw, see the edit in my previous post)

---

### Post by matt_symes on 2011-03-17
Hi

What instructions are you following. Post a link here.

If you want to boot into runlevel 1, select the recovery mode from the grub menu and select root console (single user root at runlevel 1).

You can also get there by typing 

```
sudo telinit 1
```

However, please post a link to the instructions you are following.

Kind regards

---

### Post by FastEddieLB on 2011-03-17
Wasn't getting an error, it just kept restarting right back into Gnome. I will try your other suggestion though, see if I can do it like that.

---

### Post by sisco311 on 2011-03-17
```
sudo stop gdm
```
or
```
sudo initctl stop gdm
```

See:
```
man initctl
```

---

### Post by FastEddieLB on 2011-03-17
> **sisco311 said:**
>  ```
sudo initctl stop gdm
```See:


 Thank you! This did it. ^_^

---

### Post by sisco311 on 2011-03-17
You're welcome!

Please mark this thread as [SOLVED].

---

