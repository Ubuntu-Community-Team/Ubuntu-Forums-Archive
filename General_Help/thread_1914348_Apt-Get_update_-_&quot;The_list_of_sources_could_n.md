---
title: "Apt-Get update - &quot;The list of sources could not be read&quot; error"
date: 2012-01-24
forum: General Help
---

### Post by SubZero2112 on 2012-01-24
Hey, new Linux user here, and I've run into a bit of a snag while muddling around with my /etc/apt/sources.list file. This is the error I get when I try and run sudo apt-get update.```
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/pmcenery-ppa-oneiric.list
```I don't think there's any actual problem with line 3 in the file, seeing as I've replaced the file several times in nano with a new list from the Ubuntu Sources List Generator.

I'd especially like to know why what that "d/pmcenery-ppa-oneiric.list" is there. Its the name of a bad repo I tried to add, and then (unsuccessfully) remove.

Any and all help is greatly appreciated!

---

### Post by nothingspecial on 2012-01-24
The problem isn't the file /etc/apt/sources.list but with a file in the directory /etc/apt/sources.list.d

Try removing pmcenery-ppa-oneiric.list from that folder or using ppa-purge which you can install and use in the same way as add-apt-repository.

---

### Post by SubZero2112 on 2012-01-24
Fixed! I feel like a moron...didn't even notice that folder XD. Thanks a bunch!

---

### Post by nothingspecial on 2012-01-24
No problem :)

---

