---
title: "M$ publisher"
date: 2006-06-25
forum: General Help
---

### Post by LORD_PoLvO on 2006-06-25
hey all, just need to ask because i need to use this program and i havent been able to find anything of the sort native for linux, does anyone know of a program like Microsoft publisher? because i need to use this program for school work and i never use MS Windows at home lol. please if anyone could sugest a good linux version of this program it would be helpfull. please dont say use crossover office etc etc i have tried all of these and performance is nothing to rave about and a native linux program would be so much better.

thnx, daniel

---

### Post by _simon_ on 2006-06-25
Scribus :)

Should be available via Synaptic

---

### Post by LORD_PoLvO on 2006-06-25
[QUOTE=_simon_]Scribus :)

Should be available via Synaptic[/QUOTE]



hey thnx ill give that a shot now :)

---

### Post by Declan on 2006-06-25
Yes. Scribus is very good: far better than Publisher from what I understand. I recommend going to the scribus site ([www.scribus.net](www.scribus.net)) and finding their debian repository and installing scribus-ng as well as the one from the ubuntu repositories. scribus-ng represents a more updated version.

Declan

---

### Post by LORD_PoLvO on 2006-06-25
thnx guys one last thing does anyone know where i can install extra templates etc form please?

thanks in advance, daniel

---

### Post by JoWilly on 2006-06-25
[quote=LORD_PoLvO]thnx guys one last thing does anyone know where i can install extra templates etc form please?

thanks in advance, daniel[/quote]  Have you tried the templates from the scribus download page ? (have not tried them , so I don't know if they are any good).

---

### Post by JoWilly on 2006-06-25
Here is a page where you can find the latest scibus deb packages, templates package, icc profiles, etc ...   [http://www.scribus.net/index.php?name=Sections&req=viewarticle&artid=4&page=1]("http://www.scribus.net/index.php?name=Sections&req=viewarticle&artid=4&page=1")

---

### Post by LORD_PoLvO on 2006-06-27
hey thnx

---

### Post by derek_harding on 2006-07-07
Hi,

Anyone give me the correct repositories for Scribus-ng - it's a pain trying to compile from source because of dependencies etc?

Otherwise, perhaps someone can talk me through installing -ng?

Tnx,
Derek

---

### Post by 3rdalbum on 2006-07-07
Add this line to your sources.list:
```

deb http://debian.scribus.net/debian breezy main restricted

```

Then type this at the terminal:
```

sudo apt-get update
sudo apt-get install scribus-ng

```

---

