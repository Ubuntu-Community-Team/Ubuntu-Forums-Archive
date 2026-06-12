---
title: "Software center functionality using terminal"
date: 2011-10-23
forum: General Help
---

### Post by bentley4 on 2011-10-23
Hey guys,

Does anybody know how to get a list of applications in a category(e.g.: all the applications in Accessories)like in the software center but using the terminal?

---

### Post by Gawains Green Knight on 2011-10-23
I don't know if apt-get or aptitude can do this or not.... or if synaptic can be run from command line. There presumably must be a way....

---

### Post by papibe on 2011-10-23
This is not exactly what you are looking for, but it is very useful (at least for me):
```
apt-cache search <keyword>
```
For example to look for packages related to 'unrar':
```
apt-cache search unrar
```
Regards.

---

