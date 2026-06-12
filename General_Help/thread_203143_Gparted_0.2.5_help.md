---
title: "Gparted 0.2.5 help"
date: 2006-06-24
forum: General Help
---

### Post by bellaterror on 2006-06-24
how do I install it now that I have it I dl'd it to the desktop?

---

### Post by bellaterror on 2006-06-24
tried apt-get already and it didnt work

---

### Post by moffa on 2006-06-24
The easiest way is to enable all the repositories, the multiverse and universe ones then do an ```
 sudo apt-get install gparted 
```

You can enable the repositories with ```
 sudo gedit /etc/apt/sources.list 
``` and removing the # in front of the lines that start with deb and deb-src

Hope that helps

---

### Post by Ramses de Norre on 2006-06-24
0.1 is the newest version in the repos here.. In what format did you download the 2.5 version? If you tell us we can tell you how to install it.

---

