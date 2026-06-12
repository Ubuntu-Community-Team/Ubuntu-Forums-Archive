---
title: "Cluttered software center"
date: 2011-08-31
forum: General Help
---

### Post by vpharry on 2011-08-31
[ATTACH]201162[/ATTACH]
My software center looks a bit cluttered. (See d image). What should I do 2 fix this?

---

### Post by dino99 on 2011-08-31
there is some other tools: synaptic, apt-get

---

### Post by vpharry on 2011-08-31
I use software center coz its user friendly. GeoD, Indicator... are the tabs I dont want

---

### Post by vpharry on 2011-08-31
guys plz help........

---

### Post by pAsM on 2011-08-31
> **vpharry said:**
> guys plz help........
You need to disable some PPAs from the Manage Software Sources. Once done, do a refresh and they will no longer be listed (note, you will no longer get updates from the channel). 

You may also want to run

sudo apt-get clean
sudo apt-get update

---

### Post by coffeecat on 2011-08-31
> **vpharry said:**
>  GeoD, Indicator... are the tabs I dont want

Are these 3rd party repositories you enabled? If so, you need to disable them. Software Centre -> Edit menu -> Software Sources -> Other Software Tab. Untick the ones you don't want.

---

