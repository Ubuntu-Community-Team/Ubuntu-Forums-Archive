---
title: "cant install or remove apps !!"
date: 2011-11-14
forum: General Help
---

### Post by Hidden Pain on 2011-11-14
first am newbie on kde & used gnome just for 6 months 
i cant install or remove any thing on kde interface !!!
it keep saying that i didn't provide a proper autherization !!!!

i have noticed that when am about to do some thing in gnome a password promot is shown
i think that's the problem , cause when am in kde NO password is asked

can any one help me please :(

---

### Post by oldos2er on 2011-11-14
Please don't bump your post more than once in 24hrs.

If you start muon in a terminal with **kdesudo muon** it should give you full privileges.

---

### Post by Hidden Pain on 2011-11-14
I installed  Kubuntu. I can use the desktop and applications just fine but I cannot  install anything via the muon software centre or ubuntu software centre. For example, I went to Applications >  Internet > Firefox (the icon to install it) and I got the error 
 title:"authentication error qapt batch"contet: "installer This operation cannot  continue since proper authorization was not provided".
 The problem is, the system never asked me for authorization. I know  that a box is supposed to pop up asking for my password for root access  but it doesn't appear. It's as if the OS is expecting me to give  authorization it never asks me for.I was able to do it on the command line.( kdesudo)
I'm a noob but I know enough  to "kdesudo[FONT=Verdana] [/FONT] apt-get install firefox" and that did work. :guitar:
But when I went to  install additional wallpaper, I got the same error.
Any ideas are greatly appreciated.:confused:

---

### Post by oldos2er on 2011-11-14
Looks this is a bug that was fixed before Oneiric was released: [https://bugs.launchpad.net/ubuntu/+source/qapt/+bug/833058](https://bugs.launchpad.net/ubuntu/+source/qapt/+bug/833058)
Not sure why you're experiencing it. Is your Kubuntu install fully updated?

---

### Post by Hidden Pain on 2011-11-15
yep i have the latest ver 11.10
and when i run kdesudo muon-updater from terminal
no update is available so am up to date i guess !!
-------------
note :maybe this can change your rep !! i installed the ubuntu & then installed the kde-desktop from ubuntu software center

---

### Post by BlastXng on 2012-02-28
> **Hidden Pain said:**
> yep i have the latest ver 11.10
and when i run kdesudo muon-updater from terminal
no update is available so am up to date i guess !!
-------------
note :maybe this can change your rep !! i installed the ubuntu & then installed the kde-desktop from ubuntu software center

I encountered the same issue when I installed KDE-Dekstop using
sudo apt-get install kde-desktop

Does anyone knnow when this might get fixed?

My wife uses KDE and she isn't "geek".. :D

---

