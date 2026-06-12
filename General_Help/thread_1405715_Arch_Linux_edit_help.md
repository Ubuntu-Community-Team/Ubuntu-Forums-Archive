---
title: "Arch Linux edit help"
date: 2010-02-13
forum: General Help
---

### Post by 199DMF on 2010-02-13
Hi im installing kde on my arch linux machine but i need help editing ~/.xinitrc
whenever i do
```
nano /home/myusrnme/xinitrc
```
all i get is a blank file. I need to go in that file and uncheck exec startkde, any help?

---

### Post by falconindy on 2010-02-13
If it doesn't exist, it means you didn't copy it from /etc/skel as suggested to you in the beginner's guide (which you read from start to finish, **right**?).

Or, perhaps you meant .xinitrc

---

### Post by 199DMF on 2010-02-13
> **falconindy said:**
> If it doesn't exist, it means you didn't copy it from /etc/skel as suggested to you in the beginner's guide (which you read from start to finish, **right**?).

Or, perhaps you meant .xinitrc
:-$nah didnt read the beginners guide
i just installed it and got the kde
how would i copy it? 
ill probably read it after i get kde installed

---

### Post by falconindy on 2010-02-13
Read the fine manual:

[http://wiki.archlinux.org/index.php/Beginners'_Guide](http://wiki.archlinux.org/index.php/Beginners'_Guide)

It'll answer a lot of questions.

---

### Post by 199DMF on 2010-02-13
> **falconindy said:**
> Read the fine manual:

[http://wiki.archlinux.org/index.php/Beginners'_Guide]("http://wiki.archlinux.org/index.php/Beginners%27_Guide")

It'll answer a lot of questions.
alright i will

---

### Post by 199DMF on 2010-02-13
> **falconindy said:**
> If it doesn't exist, it means you didn't copy it from /etc/skel as suggested to you in the beginner's guide (which you read from start to finish, **right**?).

Or, perhaps you meant .xinitrc
i tried ```
$ cp /etc/skel/_.xinitrc_ ~/
``` but it said it didnt have it

---

### Post by falconindy on 2010-02-13
```
$ pacman -Qo /etc/skel/.xinitrc
/etc/skel/.xinitrc is owned by xorg-xinit 1.2.0-1
```
Do you have the **xorg-init** package installed?

---

### Post by 199DMF on 2010-02-13
> **falconindy said:**
> ```
$ pacman -Qo /etc/skel/.xinitrc
/etc/skel/.xinitrc is owned by xorg-xinit 1.2.0-1
```Do you have the **xorg-init** package installed?
ill check i think i do

---

### Post by Satoru-san on 2010-02-13
just code your own .xinitrc, thats what we do in gentoo, besides they have like 3 lines.

```
 export XDG_MENU_PREFIX=gnome-
 exec /usr/bin/gnome-session

# exec enlightenment_start

#exec sawfish

#twm


export XMODIFIERS=@im=uim
export GTK_IM_MODULE=uim
export QT_IM_MODULE=uim

```

EDIT: yours will be exec startkde 

you also need to have XSESSION="KDE-4" not kde-4.3 that is in /etc/env.d/XXxsession
I dont remember the XX number off the top of my head.

---

