---
title: "ndiswrapper: remove aliases?"
date: 2006-06-10
forum: General Help
---

### Post by panurge77 on 2006-06-10
I listed my old native driver on modprobe.d/blacklist and used ndiswrapper to install de windows one. Iget this error when trying to do ndiswrapper -m:
modprobe config already contains alias directive

So I checked with "modprobe -c | grep 818x" to find those aliases:
floyd@tchs:~$ modprobe -c | grep 818x
blacklist r818x
alias pci:v000010ECd00008180sv*sd*bc*sc*i* r818x
alias pci:v00001799d00006001sv*sd*bc*sc*i* r818x
alias pci:v00001799d00006020sv*sd*bc*sc*i* r818x
alias pci:v00001186d00003300sv*sd*bc*sc*i* r818x
alias pci:v000010ECd00008185sv*sd*bc*sc*i* r818x

Maybe that's what preventing the ndiswrapper -m? How do I remove those aliases?

---

### Post by falkenberg_cph on 2006-09-19
I cant believe i can actually help someone, considering my ubuntu knowledge practically equals a big zero.

edit this file:
sudo gedit /etc/modprobe.d/ndiswrapper

Delete what needs to be deleted

---

