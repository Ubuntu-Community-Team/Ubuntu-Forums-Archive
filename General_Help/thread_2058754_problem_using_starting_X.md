---
title: "problem using starting X"
date: 2012-09-16
forum: General Help
---

### Post by dm07 on 2012-09-16
Hi,

Ubuntu 12.04
I ve got a problem with using X.

X doesn't start automatically.  I typed startx .
X  started , but software -center wasn't installed , soundcard doesn't work ,theme changed and i cannot use my USB flash for example without mounting it.

What could be the reason of this issue? 
What log have i look at , in order  to know more  about this problem?

p.s. sorry for my english

---

### Post by cwsnyder on 2012-09-16
Instead of typing **startx**, try typing **lightdm** if you are running Ubuntu.  This should take you to your GUI login screen and run the proper startup sequence.

---

### Post by dm07 on 2012-09-17
Ok. thx. It helped,but  why I don't have it start automatically??
What is possible reason?
Have I start **lightdm** command as root??

---

### Post by cwsnyder on 2012-09-22
lightdm should start automatically unless your /etc/rc.local file doesn't execute for some reason.  Check that the file exists and is executable and use[code]gksudo gedit /etc/rc.local[code]to edit the file, adding the command **lightdm** just before the last line which should say **exit 0**.

---

### Post by angry_johnnie on 2012-09-22
why do you have to run startx?

is this a minimal/net install?

if so, those apps wouldn't be installed by default.

you could try installing, for example, ubuntu-desktop, which will install everything that comes standard in a ubuntu installation.

```
sudo apt-get install ubuntu-desktop
```

if you don't want all of that, you can install whatever you need from the repositories.



also, if you do have ubuntu-desktop installed, and lightdm is simply not starting, you could use something like bum or rcconf.


```
sudo apt-get install bum
```

then run gksu bum and make sure lightdm is checked.

---

