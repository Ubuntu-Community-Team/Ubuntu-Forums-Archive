---
title: "Problem With compiling window decoration"
date: 2006-02-01
forum: General Help
---

### Post by Marsjannno on 2006-02-01
Hi, I downloaded some Window decorations from KDE Look, but now I have a little problem with compiling it- there is something wrong when i type make. I was looking for help on #kubuntu and #ubuntu but noone was able to help me there. I will put log from compiling in here. I even cant compile decorator and any other deco : [http://ubuntu.pastebin.com/532602](http://ubuntu.pastebin.com/532602) These strange letters means Error in Polish Thanks Mars

---

### Post by ykpaiha on 2006-02-01
I suppose you don't have the proper libraries **-dev installed in your system!
check for qt, kde etc..-dev as well as build essential.
you have to check your configure to see where are the mistakes
and mabe the configure must be pointing your kde (ie ./configure --prefix=/usr)

probably after some search : kdelibs4-dev should do the trick..I guess 
in synaptic or sudo apt-get install

you can try as well some feature from my own site already compiled for ubuntu at:
g.natacha.free.fr
they are a bit old but seems to work still...

---

