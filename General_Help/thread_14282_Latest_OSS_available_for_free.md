---
title: "Latest OSS available for free"
date: 2005-02-06
forum: General Help
---

### Post by MrPsycho on 2005-02-06
4Front Tech just released their formerly comercial drivers (about 2 weeks ago).  I want to upgrade for a number of reasons, but I won't list them all.

Apparantly the latest version is 3.99.2a .  
[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) 
The download page asks if I have a core compiled with "Regparm" enabled.  I can't find any mention of this as my core is precompiled.  Does ubuntu use regparm or not?

Btw I'm using optimized kernel "Linux ubuntu 2.6.8.1-4-k7".

And if you have any other advice for the update that would be appreciated! ;)
Thanks

---

### Post by GilGalad on 2005-02-06
[QUOTE=MrPsycho]4Front Tech just released their formerly comercial drivers (about 2 weeks ago).  I want to upgrade for a number of reasons, but I won't list them all.

Apparantly the latest version is 3.99.2a .  
[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) 
The download page asks if I have a core compiled with "Regparm" enabled.  I can't find any mention of this as my core is precompiled.  Does ubuntu use regparm or not?

Btw I'm using optimized kernel "Linux ubuntu 2.6.8.1-4-k7".

And if you have any other advice for the update that would be appreciated! ;)
Thanks[/QUOTE]

Regparam is not set in the Ubuntu kernels so you if it is required you will need to compile a new kernel yourself:

 > cat /boot/config-2.6.10-2-686 | grep REGP
# CONFIG_REGPARM is not set

---

### Post by MrPsycho on 2005-02-06
There is a version which doesn't require regparam.  Thanks for the info- I would have guessed the wrong file and have been in some trouble. :eek:

---

### Post by bytelab on 2005-04-13
Thanks mate! This helped me out aswell :)

---

### Post by williamx on 2005-12-05
Where is this version and how can I install it?

---

