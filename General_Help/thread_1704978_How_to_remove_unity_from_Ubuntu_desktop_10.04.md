---
title: "How to remove unity from Ubuntu desktop 10.04?"
date: 2011-03-11
forum: General Help
---

### Post by mahela007 on 2011-03-11
Just a few hours ago, I installed unity on a desktop version of Ubuntu using
sudo apt-get install ubuntu-netbook. I'm not sure I want it any more. How do I go about uninstalling this package (and the related packages)?

---

### Post by TeoBigusGeekus on 2011-03-11
Errr....
```
sudo apt-get purge ubuntu-netbook
```
?

---

### Post by searchfgold6789 on 2011-03-11
```
sudo apt-get purge unity
```
You can also use the Ubuntu software center or the Synaptic package manager ... Just do a search for unity and uninstall it.
The related packages are uninstalled automatically.

---

### Post by mahela007 on 2011-03-12
oh.. I err thought it would be more complicated than that. Hehe. 
BTW: That does the 'sudo apt-get install ubuntu-netbook' command actually install? Does it install only the unity interface or does it install other components of the Ubuntu netbook version as well?

---

### Post by oldos2er on 2011-03-12
```
apt-cache show ubuntu-netbook
``` shows quite a few dependencies and recommends.

---

