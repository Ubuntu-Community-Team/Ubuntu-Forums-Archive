---
title: "getting mesa in .deb format?"
date: 2011-03-19
forum: General Help
---

### Post by Itqan on 2011-03-19
hey where are the softwares in ubuntu's repository?
can i download mesa3d in .deb format from there?
im a noob so anyone has any ideas how to compile .tar.bz2 files (thet are call tarballs isnt it?)?

---

### Post by clhsharky on 2011-03-19
Itqan

> hey where are the softwares in ubuntu's repository?
Ubuntu Software Center or your package manager(synaptic).
> can i download mesa3d in .deb format from there?
Mesa is instaled by default, 3D dependes on your video chip.whats yours?

Terminal
```
lspci -nn | grep VGA
```
> im a noob so anyone has any ideas how to compile .tar.bz2 files (thet are call tarballs isnt it?)?
I haven't had to compile any .tar.bz2 since 10.04,look at
 
Absolute Beginner Talk , sticky
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
while waiting for better response.
Thats a good place to start for noobs.


Sharky

---

### Post by Itqan on 2011-03-19
thanxx sharky (sharky nice name lol) wow is really pre installed?
that sounds cool. i have intel integrated graphics (which dosent support glsl, per pixel lighting, all good things in life,etc).
i want mesa 3d to use its software gl feature to carry out some light work like some material nodes with real time preview. so do i have to install it again(i read somewhere that it can be compiled as software gl only) or theres some button to switch b/w hardware and software accelerated graphics?

---

### Post by Itqan on 2011-03-19
anyone pls? i wonder why my thread dies after 2-3 replies :p.

---

