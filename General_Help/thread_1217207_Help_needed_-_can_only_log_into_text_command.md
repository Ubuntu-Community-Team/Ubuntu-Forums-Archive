---
title: "Help needed - can only log into text command"
date: 2009-07-19
forum: General Help
---

### Post by ministoat on 2009-07-19
It all started when i dedcided to install fglrx drivers on 9.04 x64..

I've tried the dpkg-reconfigure xserver-xorg and this did not help, also I tried using the failsafe xorg.conf and no joy!

I can still only log into a text screen, and cannot access synaptic either, even after starting wicd manually!

any ideas? :D

---

### Post by daniel.cornea on 2009-07-19
I had the same problem and the only thing I could do is to run from life cd, backup my files and then reinstalling it, but we can wait for a while may be a more experienced user shall tell you another solution without reinstalling ubuntu

---

### Post by atomizer on 2009-07-19
there is a command-line front-end for APT, it's called aptitude.

Probably you can uninstall the wrong driver and reinstall the right one.

Then you can reconfigure X in recovery mode.

---

### Post by ministoat on 2009-07-19
thanks for the replies :)

do you know how i would use aptitude in text mode?

---

### Post by ministoat on 2009-07-19
actually I am able to use synaptic a little, but not to download new packages. I've uninstalled fglrx now, and still no xserver is starting.

---

### Post by atomizer on 2009-07-19
you are able to use synaptic..... That program is a Graphical Interface for APT, so you need X to start that program.

You mean you can type ```
apt-get remove package
```???


Are you on a wireless? would recommend a wired network, no configuration hassel in the commandline.

To use aptitude, just type ```
sudo aptitude
```

for use-instructions how to use it, read [this]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/aptitude.html").

after that, you can reboot in recovery-mode and do xfix, or 
```
dpkg-reconfigure xserver-xorg
```.


You just have to look on the net what driver you DO need instead of the fglrx drivers.

---

### Post by ministoat on 2009-07-21
thanks for the reply, but I found that it was quicker to do a reinstall!

---

### Post by atomizer on 2009-07-22
It sure is easier, but I wouldn't call a 20 minutes install and a 10 minutes update faster then 2 apt-get commands and a reboot.

But your problem is fixed, and that is what matters.

---

### Post by ministoat on 2009-07-23
funny thing is, I'm currently back at this step again, so i can put your advice into pratice, thanks :D

---

### Post by atomizer on 2009-07-24
lolz, back where you were.

It is always adviced to know your hardware ofcourse.

You can do ```
lspci
``` or ```
lshw
``` to see your hardware.

Then you can see on the internet what you need to use to get the 'shiny thingies'

Good luck!

---

### Post by ministoat on 2009-07-26
thanks for the reply - I had added a few bad lines to the xorg.conf, I was able to sort this out by using nano to delete these bad lines and all was fine :)

---

