---
title: "Quick questions about video card drivers"
date: 2011-01-08
forum: General Help
---

### Post by LetsMugSanta on 2011-01-08
Yeah so while I have mainly always installed my Nvidia driver from the driver manager provided in Ubuntu I noticed that Nvidia actually has linux versions of their drivers. The only thing is I'm not really sure if it would be compatible with Ubuntu or even let me.

In the installation instructions it asks me to install the file as root. I'm pretty newbish when it comes to using root by the way. I tried using the terminal to being root but it wouldn't let me change to the downloads area where I would have to execute it with the command they provided.

I can provide the site, video card, and driver info if necessary.

---

### Post by 3602 on 2011-01-08
Don't install any drivers if you have nVidia Optimus.

---

### Post by LetsMugSanta on 2011-01-08
It is a Nvidia Geforce 9400.

---

### Post by 3602 on 2011-01-08
Alright, could you do:
```
lspci | grep VGA
```
And paste the output?
Thanks.

---

### Post by LetsMugSanta on 2011-01-08
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8300] (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

---

### Post by LetsMugSanta on 2011-01-09
bump

---

### Post by Verbeck on 2011-01-09
whats wrong with the one ubuntu installed? 

anyway, if you want to install the driver you downloaded from the nvidia site;
* place the *NVIDIA-Linux-xxxxxx.run *in your home folder (would make it easier)
* give it execute permissions (right-click>properties>permissions>mark file...)
* switch to tty1 (ctrl+alt+F1)
* give your login credentials
* enter *sudo service gdm stop*
* enter *sudo ./NVIDIA-Linux-xxxxxx.run*
* enter *sudo reboot* when installation is complete

hope that helps

---

### Post by LetsMugSanta on 2011-01-09
When playing starcraft 2 I had some issues, so I want to see if it is the driver or if it is something else, and it doesn't hurt to have a better one anyway.

---

