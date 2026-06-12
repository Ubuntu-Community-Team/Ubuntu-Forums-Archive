---
title: "Can only boot to terminal"
date: 2009-09-16
forum: General Help
---

### Post by EoRaptor013 on 2009-09-16
I don't know what I've done, but somewhere between configuring some eye-candy for Gnome, and downloading the KDE environment with Synaptic, I have bollixed up my system. Currently, rebooting only gets me to a terminal. I do not get the Gnome, or KDE, login screen, so I have no ability to switch from one desktop environment to the other. At the command line prompt, I can enter startx, but that only takes me to Gnome, and gnome is kind of funky about running on KDM. I am certain that the default desktop environment choice is stored in some text file, somewhere, but I've searched high and low, and haven't figured out where. 

One thing, in my research, I found many references to setting the default run mode in /etc/inittab. Only, I don't got no stinkin' inittab. Maybe this got blown away, somehow?

So, how do I boot to a GUI, on one hand, and how do I change the default desktop from the command line, on the other? Oh, also, I did change the default display manager back to gdm, but that hasn't helped anything. 

Thanks, folks!

Randy

P.S. Jaunty on a Dell E1705, with nVidia 7900 card.

---

### Post by EoRaptor013 on 2009-09-16
OK, I solved part of my problem. Since all the references referred to /etc/inittab, and I couldn't find an /etc/inittab, I decided to make one. All I put in it is this: 

id:5:initdefault:

That got me to the graphical login screen where I chose Gnome, and logged in. Worked slicker 'n sn... um, oil. 

I'm still interested in knowing, however, where the default choice of desktop environment is stored. If anyone can point the way, I'd appreciate it.

Thanks!

Randy

---

### Post by wojox on 2009-09-16
On your login screen look for Options > Sessions

---

### Post by EoRaptor013 on 2009-09-16
> **wojox said:**
> On your login screen look for Options > Sessions

I'm not sure which part of my problem you are responding to, but I couldn't get to the GUI login screen without the /etc/inittab file. Of course, I realize that one can _change_ the desktop environment, once one gets to the GUI login screen (which I can, now). My question, however, is where that choice is saved. Clearly, there has to be a config file, of one sort or another, in my home directory, since this value could be different for each user. But, I can't figure out where.

Thanks for the response!

Randy

---

