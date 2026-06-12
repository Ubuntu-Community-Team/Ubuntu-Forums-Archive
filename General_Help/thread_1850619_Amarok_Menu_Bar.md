---
title: "Amarok Menu Bar"
date: 2011-09-26
forum: General Help
---

### Post by Comrde on 2011-09-26
I installed Amarok and then uninstalled it, now on my home bar(top one), it shows that Amarok is playing a song but its not and it copys whatever banshee plays. Amarok is removed but still in my menu bar.

---

### Post by raja.genupula on 2011-09-26
do this


```
sudo apt-get --purge -y remove Amarok
```


all the best.

---

### Post by Comrde on 2011-09-26
```
comrde@(none):~$ sudo apt-get --purge -y remove Amarok
sudo: unable to resolve host (none)
[sudo] password for comrde: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Amarok
comrde@(none):~$
```

I also tried to install and and run the code, same thing.

---

### Post by raja.genupula on 2011-09-27
open your synaptic pkg manager, just type amarok in the search box.you will get a list with amarok.in that select all installed amarok pkg's and mark them for remove . 


all the best.

---

