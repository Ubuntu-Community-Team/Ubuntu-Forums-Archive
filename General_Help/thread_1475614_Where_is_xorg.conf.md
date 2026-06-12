---
title: "Where is xorg.conf"
date: 2010-05-07
forum: General Help
---

### Post by satimis on 2010-05-07
Hi folks,

Ubuntu 10.04

I can't find xorg.conf on /etc/X11/

How to create it?  TIA

satimis

---

### Post by dcstar on 2010-05-07
> **satimis said:**
> Hi folks,

Ubuntu 10.04

I can't find xorg.conf on /etc/X11/

How to create it?  TIA

satimis

It is not needed any longer by the base system, it will only exist if some propriety driver creates it for its own purposes.

---

### Post by jbrown96 on 2010-05-07
xorg.conf is obsolete, unless you use AMD's FGLRX driver, Nvidia's driver, or have some specific hardware that needs xorg.conf. 

If you need to put something in there, just create the file with the relevant sections.

---

### Post by dino99 on 2010-05-07
Xorg -configure

or look nvidia-xsettings or aticonfig (depend on your driver used)

or look for xorg.conf.failsafe on hdd and rename it

---

### Post by satimis on 2010-05-07
Hi folks,

Thanks for your advice.

Actually I don't need it.  Lucid (Ubuntu 10.04) is working quite nicely after upgraded from Karmic (Ubunut 9.10).  What I'm going to achieve is follows;

I have 2 Linux PCs with XRDP and xdesktop installed.  Running rdesktop on PC-1 remotely access PC-2 (Lucid) with its desktop displayed on the former desktop but taking up the whole screen.  Now I'm trying to test whether resetting the resolution of PC-2 can solve the problem.  But I can't find xorg.conf on PC-2.  

Is there any way to reset the resolution of PC-2 ?  TIA

B.R.
satimis

---

