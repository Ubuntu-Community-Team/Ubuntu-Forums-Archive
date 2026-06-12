---
title: "Still need server GUI"
date: 2010-03-24
forum: General Help
---

### Post by rm06 on 2010-03-24
I run a headless Ubuntu file server which I access remotely via ssh or using VNC. After reboot, short of moving monitors around, is there anyway to start the GUI and continue using VNC as I normally would? I still rely on the GUI to get done what I need for the most part.

---

### Post by dcstar on 2010-03-24
> **rm06 said:**
> I run a headless Ubuntu file server which I access remotely via ssh or using VNC. After reboot, short of moving monitors around, is there anyway to start the GUI and continue using VNC as I normally would? I still rely on the GUI to get done what I need for the most part.

Why doesn't your GUI start?

---

### Post by Megafag on 2010-03-24
> **dcstar said:**
> Why doesn't your GUI start?

> **rm06 said:**
> I run a headless Ubuntu file server. 

?

---

### Post by rm06 on 2010-03-24
Sorry, there is no monitor attached, therefore I cannot log in to my server desktop.

---

### Post by lykwydchykyn on 2010-03-24
Sounds like you need to set up VNC, or one of its alternatives.

Here's a good place to start:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by dcstar on 2010-03-24
> **rm06 said:**
> Sorry, there is no monitor attached, therefore I cannot log in to my server desktop.
Set up a xorg.conf file that uses the basic vesa driver and resolution and doesn't try to autodetect anything:

[http://ubuntuforums.org/showthread.php?t=1223504](http://ubuntuforums.org/showthread.php?t=1223504)
[http://exain.wordpress.com/2009/11/19/booting-ubuntu-without-monitor-plugged-in-switched-off/](http://exain.wordpress.com/2009/11/19/booting-ubuntu-without-monitor-plugged-in-switched-off/)

---

### Post by bodhi.zazen on 2010-03-25
> **rm06 said:**
> I run a headless Ubuntu file server which I access remotely via ssh or using VNC. After reboot, short of moving monitors around, is there anyway to start the GUI and continue using VNC as I normally would? I still rely on the GUI to get done what I need for the most part.

Use an alternate VNC server , that way you will not need to log into the server first.

Better, connect with ssh -X to forward X apps or look at webmin.

---

### Post by thesenu on 2010-03-25
i think you can visit
[http://www.zeroshell.net/eng/](http://www.zeroshell.net/eng/)

---

### Post by HermanAB on 2010-03-25
Here you go:
$ ssh -X -C -c blowfish user@server gnome-panel

That will run a gnome panel on your local desktop without the need for running X on the remote machine.  Set the remote panel to auto-hide on the side of your screen to avoid confusion with your local panels and then you can go click happy and launch anything remotely for transparent display on your local desktop.

---

### Post by Gregorybekkers on 2010-03-25
Is it Ubuntu server of Ubuntu Desktop?
if it is desktop try "startx"

is it is server and you need to install a Gui

type: sudo apt-get install xubuntu
this brings a gui that requires less memory

---

