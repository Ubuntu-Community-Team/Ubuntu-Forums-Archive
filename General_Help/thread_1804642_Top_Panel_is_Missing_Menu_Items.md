---
title: "Top Panel is Missing Menu Items"
date: 2011-07-15
forum: General Help
---

### Post by UltraZone on 2011-07-15
Hello all, I'm running Comsol 4.0 and in Unity the top Panel is supposed to have the menu items of the focused application, however Unity does not create them for Comsol.  Notice the two pictures below, one running Comsol in Unity, the other one running in Gnome 2.32.  Where my File>Edit>Options>Help at Unity, huh? :D

I appreciate any input.

Unity

[IMG]http://i53.tinypic.com/2rzuhk8.png

Gnome 2.32

[IMG]http://i51.tinypic.com/2mn0ugh.png

---

### Post by UltraZone on 2011-07-15
Anybody?

---

### Post by mb36 on 2011-08-04
I just managed to get my installation of Comsol 4.2 up and running in unity and I get the same problem, so I would also be grateful for any help.

Cheers, Mårten

---

### Post by davdo2004 on 2011-08-04
Do the menu items show up in full screen mode ?

---

### Post by Starfleet on 2011-08-04
Surely...don't you just need to right click on the panel where those items would normally be and hopefully if the properties option comes up, click on it and add those items?

---

### Post by mb36 on 2011-08-04
@davdoo: No, they don't show up in full screen mode.

@starfleet: Right-clicking doesn't work for me.

And what's worse, I can't get it to work in classic Gnome either. A colleague gets that to work,just as UltraZone.

EDIT: Never mind that last complaint. I had earlier tried to get classic a bit unity-like with global menus. Disabling that brought back the menus to Comsol. Relief&#8230;

---

### Post by mb36 on 2011-08-05
After some searching I have solved the problem. Comsol is not the only program suffering from this. The solution is to deactivate global menus for that particular program. 

At the command line, write:

$ export UBUNTU_MENUPROXY=

And then start comsol:

$ /usr/local/comsol42/bin/comsol

Works for me in Unity. I hope it will work for you too.

---

