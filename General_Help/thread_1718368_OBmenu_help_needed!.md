---
title: "OBmenu help needed!"
date: 2011-03-31
forum: General Help
---

### Post by TheDexter1111 on 2011-03-31
hi all 

basically i've been setting up openbox the last couple days, and well its almost all sweet, however, I cannot for the life of me get obmenu working...

Ive installed it like the readme says to, i un-tared it in to my home dir

did:
sudo su
python setup.py install

but when i run obmenu in the terminal i get this error

root@laptop:# obmenu
/usr/local/bin/obmenu:556: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  column=gtk.TreeViewColumn("Type",renderer,text=1)
/usr/local/bin/obmenu:561: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  column=gtk.TreeViewColumn("Action",renderer,text=2)
/usr/local/bin/obmenu:566: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  column=gtk.TreeViewColumn("Execute",renderer,text=3)
Segmentation fault


I have no idea what this means.. so any help is much appreciated :)

im on
Ubuntu 10.04

---

### Post by TeoBigusGeekus on 2011-03-31
Don't use Obmenu; open the
```
~/.config/Openbox/menu.xml
```
file and edit it yourself - like a boss:P

---

### Post by TheDexter1111 on 2011-03-31
> **TeoBigusGeekus said:**
> Don't use Obmenu; open the
```
~/.config/Openbox/menu.xml
```file and edit it yourself - like a boss:P


yeah i could, but the convenience of a gui front end is its so much easier, especially for someone like me who is still relatively new to linux.. especially editing .xml files..

can you recommend a straight forward tutorial on how to do it using pipe menu's?

---

### Post by wojox on 2011-03-31
Why don't you just download it from the repo's:

```
sudo apt-get update; sudo apt-get install obmenu
```

then run "obmenu" in the terminal.

---

### Post by TheDexter1111 on 2011-03-31
> **wojox said:**
> Why don't you just download it from the repo's:

```
sudo apt-get update; sudo apt-get install obmenu
```then run "obmenu" in the terminal.

ofcourse i tried this, but still no dice.. that why its confusing

---

### Post by TheDexter1111 on 2011-03-31
in fact there seems to be a problem with them at the moment.. i cant even get bmpanel2, pypanel or tint2 from a sudo apt-get install command... i managed to get tint2 from synaptic, but im getting something like, no file found or something.
also im pretty sure i have it installed... but when i try to run it I get the error i posted in the first post.

actually.... I installed obmenu through synaptic package manager... so it should work?

---

### Post by TeoBigusGeekus on 2011-03-31
Can you post us your menu.xml file and what you are trying to do with your menus?

---

### Post by TheDexter1111 on 2011-03-31
i shall sometime tomorrow, im not near my linux box at the moment

---

