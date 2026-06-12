---
title: "I can't Remove KDE Desktop !"
date: 2010-04-21
forum: General Help
---

### Post by babin on 2010-04-21
Hi, I have a big problem !

many days ago I installed Full KDE Desktop from Synaptic in gnome Desktop, After download and install package I login with KDE Desktop !

It's my first problem : 
I could not logout again Or restart and shutdown my system, they didn't work at all, then I restart my laptop with power key !

my second problem : 
Sun java runtime didn't work in KDE desktop, and when I selected Open with other apps I couldn't find java runtime

But I logout from KDE, and now I want to use gnome desktop again, here is the big Problem !!!

many KDE apps is here that I don't need them and want to un-install them, I un-installed some from synaptic but I can't un-install them complete ! and I can't remove KDE Desktop with this command " apt-get remove kde " and in gnome Desktop java runtime still doesn't work !

I just want to remove complete KDE Desktop and I don't know what can I do ! I tried someway and searched it, but there is just one way anybody told try " apt-get remove kde " and it doesn't work for me !

:confused:

---

### Post by didkoslawow on 2010-04-21
When I want to remove KDE:
```
apt-get remove --purge kde* kdm
```

---

### Post by babin on 2010-04-21
Thanks a lot, I removed KDE desktop,

 But java runtime still doesn't work !

java runtime worked before install KDE desktop ! but now ! I can't understand what's happening here !

---

### Post by didkoslawow on 2010-04-21
What about reinstall java?

---

### Post by babin on 2010-04-21
I did it, I Un-Installed Java and installed again but there's same problem !

---

### Post by babin on 2010-04-21
I tried run my java app with " Java -jar " and it worked but It still doesn't work out of terminal !
:confused:

---

### Post by babin on 2010-04-23
nobody? :confused:

---

