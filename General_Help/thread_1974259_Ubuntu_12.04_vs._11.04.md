---
title: "Ubuntu 12.04 vs. 11.04"
date: 2012-05-05
forum: General Help
---

### Post by ngrieb on 2012-05-05
Hi all, 

I am thinking of upgrading my desktop pc from 11.04 to 12.04 for a few reasons (mainly GIMP 2.8 ). I was just wondering if there are any main drawbacks to doing this (Other than the Unity interface, which I am not very thrilled about, but can live with).

I like to create 3D renderings and art with Blender, Inkscape, GIMP, etc, and enjoy playing Steam games using WINE (graphically and memory intensive things). Are there any noticeable graphics/memory performance issues associated with the upgrade that anyone can tell me about? I'm running a Core i7 870, and an nVidia GForce GTX 560 Ti, and 8GB of PC1600 RAM.

Thanks for the advice.

---

### Post by Bandit on 2012-05-05
Hmm Gimp2.8 still isnt in repos that I am aware of. At least not the normal ones. Also if you use a drawing tablet like I do you may want to wait until GIMP 2.8 is fully GTK3.

---

### Post by mordoc on 2012-05-05
> **ngrieb said:**
> Hi all, 

I am thinking of upgrading my desktop pc from 11.04 to 12.04 for a few reasons (mainly GIMP 2.8 ). I was just wondering if there are any main drawbacks to doing this (Other than the Unity interface, which I am not very thrilled about, but can live with).

I like to create 3D renderings and art with Blender, Inkscape, GIMP, etc, and enjoy playing Steam games using WINE (graphically and memory intensive things). Are there any noticeable graphics/memory performance issues associated with the upgrade that anyone can tell me about? I'm running a Core i7 870, and an nVidia GForce GTX 560 Ti, and 8GB of PC1600 RAM.

Thanks for the advice.

I'm at the far lower end of the computer scale (Atom with 2GB of RAM and an Intel 945 for video) and can't say I notice much of difference.

---

### Post by ngrieb on 2012-05-05
Mordoc,

I am concerned because I installed 11.10 on my Toshiba NB305 netbook, and the speed of everything seems to have decreased massively from 10.04. I have been unable to upgrade it to 12.04 because of some kind of authentication error...a story for a different thread perhaps.

---

### Post by kio_http on 2012-05-06
> **ngrieb said:**
> Mordoc,

I am concerned because I installed 11.10 on my Toshiba NB305 netbook, and the speed of everything seems to have decreased massively from 10.04. I have been unable to upgrade it to 12.04 because of some kind of authentication error...a story for a different thread perhaps.

From my experience. 11.10 was unusable on my Atom 2GB RAM Intel 945 graphics system. 12.04 works and is usable but not the best performer.

KDE however is lightning fast on both 11.10 and 12.04 with all desktop effects. Maybe Gnome 3x isn't mature enough. But according to me compiz has a lot of flaws and tying Unity to it is not a good idea.

---

### Post by wolfen69 on 2012-05-06
> **kio_http said:**
> From my experience. 11.10 was unusable on my Atom 2GB RAM Intel 945 graphics system. 12.04 works and is usable but not the best performer.

KDE however is lightning fast on both 11.10 and 12.04 with all desktop effects. Maybe Gnome 3x isn't mature enough. But according to me compiz has a lot of flaws and tying Unity to it is not a good idea.

Then use what works....whether it's windows or mac. Your family is more important

---

### Post by mips on 2012-05-06
If you want to use 12.04 I suggest you do a clean install from the alternate cd image.

To install gimp 2.8
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

---

### Post by philinux on 2012-05-06
Moved to general help forum.

If OP needs single window mode stable gimp then see this.

[http://www.webupd8.org/2011/06/gimpbox-get-single-window-mode-in.html](http://www.webupd8.org/2011/06/gimpbox-get-single-window-mode-in.html)

---

