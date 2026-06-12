---
title: "Alternatives to GDM?"
date: 2010-02-11
forum: General Help
---

### Post by chaanakya_chiraag on 2010-02-11
Hey guys!
I was wondering what lightweight alternatives to gdm exist.  I would love to stay away from kdm as that would bring in all the kde dependencies and fill my hard drive with crud.  Furthermore, I'm running fluxbox, so I want to keep the login as light as possible.  With that in mind, could someone please give me a list of alternative desktop managers that have the following features:
Multiple sessions
Able to switch sessions on-the-fly
Loads quickly

Thanks!
- Chiraag

---

### Post by VCoolio on 2010-02-11
There are a lot, none of which I was able to get properly going on ubuntu. xdm, slim, cdm (in bash, by an arch guy; search the archlinux forum for it), entrance (e17, buggy and afaik unmaintained), lxdm (for lxde, pretty alpha still).

---

### Post by chaanakya_chiraag on 2010-02-11
So they exist, but are quite hard to get set up on Ubuntu?

---

### Post by chaanakya_chiraag on 2010-02-15
You know what?  Heck with it! I'm gonna disable gdm and xorg from starting at boot and I'm gonna run startx :) Marking thread solved.

---

### Post by MooPi on 2010-02-15
I use xdm with my Openbox system. Works wonderfully  and easy to set up. Simply edit the /etc/X11/xdm/Xresources file for custom colors, login picture, and welcome phrase. Options that affect function are a different story. It just lets you login and that is it.

---

### Post by chaanakya_chiraag on 2010-02-16
I basically set up a custom .xinit and .Xresources to set the DPI manually (startx wasn't setting the correct DPI) and run startx.  I don't really care for graphical login managers anymore :D  Thanks anyway though.  I'll be sure to use that if I ever decide to go back to a graphical login :lol:

---

### Post by Locutus_of_Borg on 2010-02-16
i know thread is solved, but qingy is great
its light as hell
can use text mode or graphical
saves sessions
has the advantage of being easier to load different sessions over startx
easy to install and setup

---

### Post by Simian Man on 2010-02-16
I really love Slim.  It is simple, looks good, is easy to theme and is pretty much perfect for a simple login manager.  I don't know how easy it is to use in Ubuntu though.

---

### Post by jaezcurra on 2010-02-16
Hi, I would give wattOS a try: [http://www.planetwatt.com/](http://www.planetwatt.com/)
Good luck :)

---

### Post by chaanakya_chiraag on 2010-02-16
If anyone can give me the repo for SLiM, that would be great, as I can't find it in the repos :(  It's just for future reference.  Thanks!  Also, does anyone know how to prevent X from starting at boot?  Would it just be ```
sudo update-rc.d -f x11-common remove
```?  Thanks!
- Chiraag

---

