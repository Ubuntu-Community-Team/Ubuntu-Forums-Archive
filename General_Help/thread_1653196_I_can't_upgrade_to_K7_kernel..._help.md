---
title: "I can't upgrade to K7 kernel... help"
date: 2010-12-26
forum: General Help
---

### Post by paragdulam on 2010-12-26
HI!!

I have core i5 4GB RAM but i have installed i386 ubuntu 10.10. i am trying to install k7 kernel so that the all ram should be utilised. i used sudo apt-get install linux-k7-smp command on terminal.

its not workin....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-k7-smp


pl z help..

thanks in advance...

---

### Post by Monotoko on 2010-12-26
From what I have read here: [http://ubuntuforums.org/archive/index.php/t-826796.html](http://ubuntuforums.org/archive/index.php/t-826796.html)

The k7 kernel was either dropped or combined into the linux-generic package. You may want to look at PAE (Physical Address Extension) instead.

---

### Post by dino99 on 2010-12-26
all your ram will be used if you install the generic-pae kernel instead of the generic (do it with synaptic), but your bios need to be set of course to use pae

---

