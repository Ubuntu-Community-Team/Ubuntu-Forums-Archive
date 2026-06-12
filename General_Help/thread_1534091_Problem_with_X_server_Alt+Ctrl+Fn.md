---
title: "Problem with X server Alt+Ctrl+Fn"
date: 2010-07-19
forum: General Help
---

### Post by a.kazemi on 2010-07-19
Hi dears,
I want to exit from X server and run a Nvidia Graphic driver installation in tty1 mode because installation stop with the error that says you have to exit X server first. but now when I press Alt+Ctrl+f1 to exit the X server I see very Unidentified characters and symbols in various colors and I can't do anything! the keyboard doesn't work and I have to turn of PC by holding shutdown  button.

please help me what is going on?

---

### Post by gnik1 on 2010-07-20
I have this same problem. How do I stop the x-server. This is the only relevant thread about it. During nvidia driver installation it asks that I stop the x-server.

---

### Post by gnik1 on 2010-07-21
I was able to get it installed after downloading the latest driver and following these commands posted in another thread:

Kill X
Now, it's time to stop X and the gdm (or kdm for Kubuntu Users)
This requires that you logout and switch to another tty console ( Ctrl+Alt+F1 ).

Login to the shell, and kill gdm:
Code:

sudo /etc/init.d/gdm stop

This may take a while to complete.

In some rare instances, stopping gdm won't stop Xorg, due to the Xsession being busy with whatever error has occurred (Ubuntu goes into Low Resolution mode, X failed to start, etc).
In these instances, it is required that you run a kill of Xorg before you can continue with the installation of the driver.
Code:

sudo killall Xorg


Installing NViDIA
Afterwards, its time to install the drivers.

sudo sh NVIDIA-Linux-x86_64-256.35.run

---

