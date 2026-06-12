---
title: "how to tell ubuntu to prefer one repo over another ??"
date: 2010-06-18
forum: General Help
---

### Post by lion21 on 2010-06-18
consider php5 is present in two repo  , urls of both these repo are present in /etc/sources.list , 

now if I do 
apt-get install php5  

which one will get installed ??


I am on ubuntu 9.04 , apt-cache show php5 , gives the version php5.2.4,  but I want to upgrade it to php5.3 .

Thanks in Advance.

---

### Post by yeleek on 2010-06-18
look at 

man apt_preferences

---

### Post by WorMzy on 2010-06-18
If you open Synaptic, then you can "force" the version you want installed. You can probably do this via command line too, but you'd need to look at the man pages for an explanation of how.

---

