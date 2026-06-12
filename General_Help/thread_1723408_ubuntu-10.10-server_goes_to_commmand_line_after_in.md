---
title: "ubuntu-10.10-server goes to commmand line after installation"
date: 2011-04-07
forum: General Help
---

### Post by ummairt on 2011-04-07
I have installed ubuntu-10.10-server-amd64 by using virtual box for testing purposes. After installation and setting in grub i choose linux server from the menu and get login prompt on the command line..After login it stays on the command line...

Do I have to install a desktop env ? If yes how ?

I would appreciate it if you could help me....
Thank you.

---

### Post by cobolt01 on 2011-04-07
```
sudo apt-get install gnome-desktop-environment
```

---

### Post by LewRockwellFAN on 2011-04-07
> **ummairt said:**
> 
Do I have to install a desktop env ?.
Only if you want one.

QUOTE=ummairt;10647808]
 If yes how ?[/QUOTE]
Might be easiest to start with the desk top iso. If you want to do it from the desktop hang around and someone more familiar with it will give you the exact commands if you haven't already found them. I believe you might start with
man apt
because I think apt is what you will use to get some more aps. You might start by getting synaptic and then you can look for a desktop. I think maybe nautilus and gnome and their dependencies might do it.

---

### Post by LewRockwellFAN on 2011-04-07
Thanks, Cobolt. You type a might faster than me. 0 replies when I started. I suppose that would work on the mini-remix version too. I kind of want to play with that. :)

---

### Post by ummairt on 2011-04-07
Thank you very much guys :)

---

### Post by ummairt on 2011-04-07
Ive got another question related to this installation. Now I have the ubuntu desktop env which i think is gnome. In order to display the image from virtual box in fullscreen I think i will be needing a display driver which the "additional drivers manager" doest not find... Any solution to that ?

---

### Post by LewRockwellFAN on 2011-04-20
> **ummairt said:**
> Ive got another question related to this installation. Now I have the ubuntu desktop env which i think is gnome. In order to display the image from virtual box in fullscreen I think i will be needing a display driver which the "additional drivers manager" doest not find... Any solution to that ?
Try posting here:
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by collisionystm on 2011-04-20
You should have just used Ubuntu Desktop if you wanted a GUI. Server only gives you a few features default that you normally would have to download manually with destkop. You wont even notice these. Open terminal, type tasksel choose ubuntu desktop and hit ok. It converts it over.
 
As far as virtualbox, install guest additions. I get the feeling you are going to have issues with your install though. Just installing the gnome desktop enviroment by itself is a bit of a hack job.

---

