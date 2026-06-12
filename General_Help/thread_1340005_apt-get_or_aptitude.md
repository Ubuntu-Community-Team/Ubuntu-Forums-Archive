---
title: "apt-get or aptitude?"
date: 2009-11-28
forum: General Help
---

### Post by manuleka on 2009-11-28
i've come across sudo and gksudo... then installing softwares through command line i come across apt-get and aptitude, what are the difference between the two?

---

### Post by jimfuture12345 on 2009-11-28
Hi , read inside decumentation it is explained

---

### Post by Virtual Liberty on 2009-11-28
There's almost no difference between them ( [explanation]("http://www.psychocats.net/ubuntu/aptitude") ).

---

### Post by etnlIcarus on 2009-11-28
Supposedly aptitude can better resolve dependency issues and is recommended for larger upgrades, although I can't verify this. Aptitude's syntax is a little bit cleaner, too (eg. aptitude's -R argument, vs. apt-get's rather long and Engrish --no-install-recommends).

---

### Post by manuleka on 2009-11-28
ok so aptitude and apt-get does pretty much the same... i just thought aptitude would do cleaner package management but it seems like apt-get does the same on newer versions of ubuntu

---

### Post by shaggy999 on 2009-11-28
aptitude has a curses-based interactive session for browsing through packages (think synaptic for command line) and doing advanced package management like pinning packages. That's the major difference.

---

### Post by bapoumba on 2009-11-28
They do not share history files, so please do not mix the two ;)

---

### Post by manuleka on 2009-11-28
> **bapoumba said:**
> They do not share history files, so please do not mix the two ;)

wow... i installed deluge on synaptic then removed them with aptitude... 

it seems to pickup the dependencies alright... 

so what do you guys recommend? apt-get or aptitude?

---

### Post by seeker5528 on 2009-11-28
When GUI is available I prefer Synaptic, if I am at the command line and want something a little more tab completion/search friendly I prefer aptsh.

[http://aptsh.berlios.de/howto.html](http://aptsh.berlios.de/howto.html)

Later, Seeker

---

