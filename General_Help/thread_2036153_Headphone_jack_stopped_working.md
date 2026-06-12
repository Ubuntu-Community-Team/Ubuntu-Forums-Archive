---
title: "Headphone jack stopped working"
date: 2012-08-01
forum: General Help
---

### Post by Acradon on 2012-08-01
Hi there, 

I am running Ubuntu 12.04 and this morning when I tried to use Skype the headphones didn't have sound. I tried my speakers and also no sound. However, the built in speakers of the laptop work. but cuit out once a jack is connected. It reckognises the headphones or the speakers, but no sound. And yes, the volume is up. 

Any ideas. I think my skype updated too, but the problem malso persists for Banshee and other sound related programs

Greetz

Acradon

---

### Post by krustenBrot on 2012-08-01
I sometimes have problems with the pulseaudio daemon not recognizing my speakers connected through HDMi.
Maybe this works for you as well:
Open up a terminal and type
```
 pulseaudio --kill 
```
the daemon should stop now restart it by typing
```
pulseaudio --start 
```
Hope it helps. :)

---

