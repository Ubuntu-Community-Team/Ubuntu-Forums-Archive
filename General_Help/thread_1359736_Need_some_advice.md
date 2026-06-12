---
title: "Need some advice"
date: 2009-12-20
forum: General Help
---

### Post by dk666 on 2009-12-20
I have a friend ask me to help them their church that has been using windows 98 as a straight internal file server through shares its been really slow and keeps dying. I think I can build a better system.
 
They now have 10 windows workstations that share files. Can anyone recomend;
 
A inexpensive computer setup that will meet their needs I have an external DVD-R for backups I beleive its a memorex USB 2.0. 
 
I am new to Ubuntu and have only been using it for a couple of months but its fast and works well. Would I need the server version ?
 
Cheers,
 
DK

---

### Post by JT9161 on 2009-12-20
You don't have to, but it would be an obvious choice, normal Ubuntu likely would take up more space than would be needed, there is also the option of something like Debian Stable. 

As far as hardware goes harddisk and network speed seem to be obvious, a big 7200 RPM disk is nothing new and a gigabit network card should meet their traffic needs (If it's not obvious i'm suggesting a custom build instead of a pre-built machine)

---

### Post by 3rdalbum on 2009-12-20
> **dk666 said:**
> 
They now have 10 windows workstations that share files. Can anyone recomend;
 
A inexpensive computer setup that will meet their needs I have an external DVD-R for backups I beleive its a memorex USB 2.0.

Whatever the cheapest computer you can find is, that will work. A nettop works really well (I built my own Atom-based nettop to use as a home server).

> I am new to Ubuntu and have only been using it for a couple of months but its fast and works well. Would I need the server version ?

No - the server version is the same as the desktop version, except without a GUI. Install the desktop version (as you're a new user) and then install the "system-config-samba" package. Set up your network shares with System > Administration > Samba, reboot the clients and you've got yourself a server.

---

### Post by dk666 on 2009-12-20
Awesome Thanks
 
 
I have a Christmas Project...... Woo Hoo

---

### Post by bodhi.zazen on 2009-12-20
> **3rdalbum said:**
> No - the server version is the same as the desktop version, except without a GUI. 

Well, not exactly. The server version is much lighter and takes up much less space on the HD, the installer offers different options, and the server kernel is customized (optimized) for serving files.

I would advise setting up the server version and then, if you want a graphical interface, take a look at webmin.

---

