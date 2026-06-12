---
title: "Amarok+Shouter"
date: 2006-02-08
forum: General Help
---

### Post by Kosmonaut on 2006-02-08
Hi Ubunturistas!

There is a script for amarok called shouter [http://kde-apps.org/content/show.php?content=22170](http://kde-apps.org/content/show.php?content=22170)

It seems to be cool! But it isn't working with Kubuntu (kde3.5.1).

Everytime I want to start it, amarok tells me: "Das Skript "Shouter.py" beendete mit dem Fehlerkode: 1" (-> The Skipt"shouter.py ended with the ErrorCode:1).

Details says Traceback (most recent call last):
File "/home/bernd/.kde/share/apps/amarok/scripts/shouter/Shouter.py", line 24, in ?
from StreamController import *
File "/home/bernd/.kde/share/apps/amarok/scripts/shouter/StreamController.py", line 23, in ?
from StreamPublisher import *
File "/home/bernd/.kde/share/apps/amarok/scripts/shouter/StreamPublisher.py", line 23, in ?
from Publisher import *
ImportError: No module named Publisher

Ok what does that mean? Any Ideas? Is there someone out there, who can use shouter.py? Am I the only one with this strange error?

*Never mind my "english", I'm from bavaria*

---

### Post by Kosmonaut on 2006-02-10
Noone?!?:-k

---

### Post by 0xBulbizarre on 2006-02-11
hello, I never used shouter, nor do I use amarok frequently, but

some dependencies are missing it seems:

> ImportError: No module named Publisher

try to find a package that could fix it !

how ?

go to shouter website, try to find what are the dependencies, then install using apt-get adept or synaptic!

hope this helps !

---

### Post by pkulak on 2006-04-27
You need to find Shouter.py (just do a locate) and make a link to it in the folder where Amarok installed Shouter.

---

### Post by Kosmonaut on 2006-04-27
You are right!

The missing Publisher.py and Zeroconf.py are located in
/usr/share/apps/amarok/scripts/common/
Just make a link of those to files in 
/home/*USER*/.kde/share/apps/amarok/scripts/shouter/ 

then the shouter script should run well. 
BTW: Now that the script works, it seems to be quite buggy :rolleyes:

---

