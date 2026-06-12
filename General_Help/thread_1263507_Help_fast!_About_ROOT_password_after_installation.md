---
title: "Help fast! About ROOT password after installation"
date: 2009-09-11
forum: General Help
---

### Post by mac666 on 2009-09-11
Hey
When i install Ubuntu on my computer, i get a really small resolution, like 640x400 or something - unabling me to see all the entire window...

But i was able to install it, how ever i never saw anything about the root password,
this is the secound time i reinstall it just for that matter!
How do i get my root password, since i didnt set it in the first place?!

---

### Post by nikhilbhardwaj on 2009-09-11
you don't have a root password in ubuntu 
use sudo instead

let 'abc' command asks for root password
run it as
sudo abc
then enter your password

---

### Post by mac666 on 2009-09-11
but what about when i need to chmod, chown, install drivers, edit  config files that are roots?
BTW Thanks for quick reply!

---

### Post by cak3 on 2009-09-11
when you run a command with "sudo" you are executing that command as root. (as long as your user has permission to do so, and the default user created on installation does). There actually is a root account, its just disabled by default for security reasons, since you can run anything as root by using sudo. If for some reason you need a root prompt, you can do that with the command "sudo su"

---

### Post by nothingspecial on 2009-09-11
See [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

---

### Post by mac666 on 2009-09-11
thanks guys... seems all along ive been abusing mr Root when i didnt need to...

Thansk again!!

---

### Post by warroomcbw on 2009-09-12
> **cak3 said:**
> when you run a command with "sudo" you are executing that command as root. (as long as your user has permission to do so, and the default user created on installation does). There actually is a root account, its just disabled by default for security reasons, since you can run anything as root by using sudo. If for some reason you need a root prompt, you can do that with the command "sudo su"

Well folks, I still am confused.   I need to change config. files for pulse audio and some others.
They are locked or forbidden.  I need to save them to their original directories and write over the original files.
But to do this I need root permissions.  I don't know how to use the terminal commands to do this if I log on as "sudo".  Am I making this too hard?    I'm fine with the terminal when all I have to do is cut and paste.  But when I have to tell it what to do with itself......well it's not like the old DOS commands I knew way back.

Little help please?

---

### Post by Vaphell on 2009-09-12
sudo gedit - it will launch editor with root priviledges, so you can edit stuff in system directories.

sudo before actual command runs that command as root

---

### Post by aysiu on 2009-09-12
> **Vaphell said:**
> sudo gedit - it will launch editor with root priviledges, so you can edit stuff in system directories.

sudo before actual command runs that command as root
```
gksudo gedit
``` not *sudo gedit*

Good to get into the habit of using *gksudo* with graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2009-09-12
> **Vaphell said:**
> sudo gedit - it will launch editor with root priviledges, so you can edit stuff in system directories.

sudo before actual command runs that command as root
```
gksudo gedit
``` not *sudo gedit*

Good to get into the habit of using *gksudo* with graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Vaphell on 2009-09-12
yes i know that GUI apps should be launched with gksu, but in case of gedit it doesn't really matter.

in general:
- sudo for terminal based apps
- gksudo for GUI apps

---

### Post by aysiu on 2009-09-12
> **Vaphell said:**
> yes i know that GUI apps should be launched with gksu, but in case of gedit it doesn't really matter.

in general:
- sudo for terminal based apps
- gksudo for GUI apps You can do whatever you want on your own machine. But if you start posting *sudo gedit* on the forums for other users to see, new users see that and think "Great. If I need to escalate privileges for a graphical application, I just put *sudo* in front of it." Next thing you know, some new user is trying to update Firefox and uses *sudo firefox* and has all sorts of weird permissions issues.

Instead of keeping track of which graphical applications are "okay" with *sudo*, just get in the habit (at least on these forums, if not on your own Ubuntu installation) of writing *gksudo gedit*. Better to get folks in the habit of seeing *gksudo* with graphical applications and *sudo* with terminal ones.

---

