---
title: "memory usage"
date: 2010-01-26
forum: General Help
---

### Post by symon1980 on 2010-01-26
hey all.....
Just installed Ubuntu on my gf's desktop....

when i check the system monitor it says im using 262mb of the 865mb Ram that its got... but.....
when i launch a terminal and type "free -m" the output contridicts that..


fleur@fleur-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           875        670        205          0         52        354
-/+ buffers/cache:        263        611
Swap:         2565          0       2564


what the hell? one of them is not true... I would tend to trust the terminal more than a gui... but if this was true... Ubuntu 9.10 is using a hell of alot of ram even when idle.....

any thoughts?

---

### Post by OrangeCrate on 2010-01-26
**Linux Memory Management**

[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

---

### Post by symon1980 on 2010-01-26
fair enough... i guess I should be looking at the buffer/cache line... thanx

a second query... is it normal for ubuntu to use 
14.9mb for nautilus
6.1 mb for python
5.8mb! for gnomepanel!

seems quite high for such small apps...? or is it just me? :p

---

### Post by t4thfavor on 2010-01-26
It's cache, don't worry about it, everything is working as it should be.

---

### Post by warfacegod on 2010-01-26
> **symon1980 said:**
> fair enough... i guess I should be looking at the buffer/cache line... thanx

a second query... is it normal for ubuntu to use 
14.9mb for nautilus
6.1 mb for python
5.8mb! for gnomepanel!

seems quite high for such small apps...? or is it just me? :p

It's normal. When Ubuntu uses RAM as Cache it will almost immediately give up enough of the cache to make room for whatever app you decide to run or an already running app that asks for more real RAM

---

### Post by symon1980 on 2010-01-26
aight... cool. 
cheers guys

---

