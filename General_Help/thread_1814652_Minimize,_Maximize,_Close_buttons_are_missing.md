---
title: "Minimize, Maximize, Close buttons are missing"
date: 2011-07-29
forum: General Help
---

### Post by DerekConnor on 2011-07-29
As title states, they are missing, and from every window. I have googled this and found fixes but in doing some of the "fixes" the bar at the top of the screen disappears and docky becomes effectless. if you can help me I'd love you forever.


**Also, I run Ubuntu 11.04 NN

---

### Post by Matt 6:27 on 2011-07-29
Mine aren't missing, but they don't seem to work anymore since today's update came in. Mouse buttons work on some stuff, but not others.  Keyboard controls allow me to get around a screen, but it's not an ideal fix.  Anyone else lose ability to use max, min & close buttons?  I'm running Lucid (10.04 LTS)

---

### Post by XubuRoxMySox on 2011-07-30
It may be a theme thing. I'm using Xubuntu 10.04 and have not had anything b0rked by an update (yet - fingers crossed). Try using a different *theme* in your Ubuntu. It might even work again if you switch back afterwards.

Hoping,
Robin

---

### Post by 73ckn797 on 2011-07-30
From a terminal enter:
```
gconf-editor
```
Go to apps/metacity/general/button layout
if nothing is there then click on it and enter:
```
close,minimize,maximize:menu
```


See if that will work.

---

### Post by pqwoerituytrueiwoq on 2011-07-30
```
gtk-window-decorator  --replace
```
that should fix it

---

### Post by DerekConnor on 2011-08-01
Thanks everyone for the help, but nothing here suggested worked :\

---

### Post by ninjaaron on 2011-08-01
do you have window decorations enabled in compiz?

---

### Post by DerekConnor on 2011-08-01
^Fixed it man, thanks much.

---

### Post by WhoCanHelpMe on 2012-03-09
Plus if your windows is barely stuck under top bar and you don't have buttons you could also turn on "Windows position" in compiz so they would launch in the center. Helped me to "fix" that problem.

---

### Post by NikolaSamr on 2012-03-09
îáñëóæèâàíèå êîíäèöèîíåðîâ â ìîñêâå - [http://tkf-climat.ru/obsluzhivanie_kondicionerov](http://tkf-climat.ru/obsluzhivanie_kondicionerov) - îáñëóæèâàíèå êîíäèöèîíåðîâ â ìîñêâå

---

