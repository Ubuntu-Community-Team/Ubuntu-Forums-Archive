---
title: "Is it ok to stop compiz from running on a server?"
date: 2012-09-18
forum: General Help
---

### Post by clay7 on 2012-09-18
Hello,

I have a box with Ubuntu 12.04 LTS that originally was used as a desktop PC but now it is a server. compiz is taking up a lot of CPU resources. Is it ok to stop compiz? Would doing so cause problems on the server?

The server is offsite and I'm using SSH to get to it. I could stop it in htop if needed.

(Posted in General because, although this is a server, it was originally configured as a desktop and is still used as a desktop on rare occasions)

---

### Post by newb85 on 2012-09-18
Compiz is used by your Desktop Environment and Window Manager.  If you're using the machine as a headless server, you shouldn't need any of that.

---

### Post by iponeverything on 2012-09-18
turning off compiz, won't cause problems if you don't need the gui

---

### Post by clay7 on 2012-09-18
I tried to kill it in htop, but it sprang back to life. But, kill -9 xxxx did it. Everything else seems to be running fine.

Just wanted to be sure before I caused a potential interuption in service. Thanks!

---

### Post by Wim Sturkenboom on 2012-09-19
You can modify the grub configuration so it boots to a console instead of a graphical environment.

Taken from another post:
> **f8l_0e said:**
> Ok, try this.  Edit /etc/default/grub 
change the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="[COLOR="Red"]*text*[/COLOR]"

then run sudo update-grub2

I've added the word 'text' (red italic)

---

### Post by dcstar on 2012-09-19
> **clay7 said:**
> I tried to kill it in htop, but it sprang back to life. But, kill -9 xxxx did it. Everything else seems to be running fine.

Just wanted to be sure before I caused a potential interuption in service. Thanks!

Uninstall all the useless Compiz packages.

---

