---
title: "How Do I Increase Graphics Performance?"
date: 2006-06-05
forum: General Help
---

### Post by Blarion on 2006-06-05
Any ideas are welcome.

---

### Post by xXx 0wn3d xXx on 2006-06-05
Use Dri, use the latest drivers for you video card, overclock your vc, decrease graphics down lower, (16-8) and that's all I can think of.

---

### Post by mattkenn4545 on 2006-06-06
This would prob do it :)

[http://www.nvnews.net/previews/geforce_7950_gx2/index.shtml](http://www.nvnews.net/previews/geforce_7950_gx2/index.shtml)

What have you done so far what card etc...

---

### Post by bluevoodoo1 on 2006-06-06
bluevoodoo1@ubuntu:~$ apt-cache search overclock
nvclock - Allows you to overclock your nVidia card under GNU/Linux

Haven't tried it though.

What video card do you have?

---

### Post by kuja on 2006-06-06
This is an easy question to answer, hehe
Buy a better video card! Never fails.

---

### Post by Blarion on 2006-06-06
Uh, I have a Geforce 6600 GT.

---

### Post by bruce89 on 2006-06-06
Use Epiphany instead of firefox!

---

### Post by Denis on 2006-06-06
If you mean 2D graphics, for your desktop. 

You could try experimenting wih XGL/compriz: [http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl%2Fcompiz](http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl%2Fcompiz)

I don't know about 3D performance and games.

---

### Post by mlind on 2006-06-06
Use nvidia proprietary drivers. And you need to disable DRI module from xorg.conf
if you're doing so, otherwise performance is pretty bad.

---

### Post by Blarion on 2006-06-06
Nvidia GLX?

---

### Post by mattkenn4545 on 2006-06-06
Yes, just disable dri in the xorg config file and use 'nvidia' for the driver (see the wiki it has all you need.

---

### Post by kuja on 2006-06-06
[QUOTE=Blarion]Uh, I have a Geforce 6600 GT.[/QUOTE]
That's not a bad card at all really, but I did notice a difference when I put in a 7600GT a couple weeks ago. One thing worth trying is playing around with things in the program nvidia-settings, which you can install with ```
 sudo apt-get install nvidia-settings
```, this of course, is assuming you've already installed the package nvidia-glx ```
 sudo apt-get install nvidia-glx 
``` After installing nvidia-glx, run the program ```
 sudo nvidia-xconfig 
```, reboot, and you should be golden. All sorts of things you can do really.

---

### Post by Blarion on 2006-06-06
Uh, when I tried to install nvidia-settings it tried to delete nvidia-glx.

---

### Post by kuja on 2006-06-06
[QUOTE=Blarion]Uh, when I tried to install nvidia-settings it tried to delete nvidia-glx.[/QUOTE]
Umm, skip that part then, I think you may very well be able to run the program without having to install anything extra, it might be included in nvidia-glx?

---

### Post by mlind on 2006-06-06
nvidia-settings is now included in nvidia-glx package.

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by Blarion on 2006-06-06
Woah, nvidia-settings really boosted my framerates with some tweaking, thanks a bunch. Pretty user-freindly too.

---

