---
title: "package problem. cant update..."
date: 2009-12-23
forum: General Help
---

### Post by sapple on 2009-12-23
Hi, I recently installed ubuntu 9.04 to a friends notebook, and completly removed windows from her computer, telling her that ubuntu is enough for everything.

I installed some usufull progams and packages, taught her the basics and everything was working ok. She was able to surf, watch videos, etc...


But yesterday she called me and she said she cant watch facebook videos, and i talled her to install ubuntu restricted packages. she did so, but then even bigger problems arise.. I cant understand why, here are the problems:

1) she cant synaptic, she says it opens and disappears immediatly.

2) when she opens add/remove packages,, she gets an error message, saying something about the packages is wrong..

3) she cant start gksu nautilus..   when she types it, the root window doesnt open uo



I told her to type :  sudo apt-get update,  and sudo apt-get install -f

the first one worked, but the second one gave an error saying that it is locked, some other synaptic is open, but none is..


i sent her my sources.list file, and she replaced it with hers, but it didnt solve the problem..



So now, basicly she cant do any kind of updates. something is wrong with the sources but, icant figure out how to fix, 


any help?

---

### Post by sapple on 2009-12-23
any ideas? basicly, i want to be able to reset my package sources.. add/remove should then work.

this is what i get: 
The package sun-java6-bin needs to be reinstalled, but I can't find an archive for it.

---

### Post by sapple on 2009-12-27
ok i solved the problem.. basicly removed those jre packages one by one. then executed  apt-get update   and   apt-get install -f     , the problem was solved.

However, still cant acces to snaptic from gnome, i can open it from terminal.

---

