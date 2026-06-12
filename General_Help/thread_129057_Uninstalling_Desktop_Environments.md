---
title: "Uninstalling Desktop Environments"
date: 2006-02-12
forum: General Help
---

### Post by ivanhelguera on 2006-02-12
Hi, 
How to uninstall completely Ubunutu/Kubuntu/Xubuntu? I mean not the entire system, but  all the files that went with the respective *-desktop packages. 
IH

---

### Post by newuser111 on 2006-02-12
if you install debfoster it will show you which meta package is keeping which packages installed

---

### Post by Adrian on 2006-02-12
[QUOTE=ivanhelguera]Hi, 
How to uninstall completely Ubunutu/Kubuntu/Xubuntu? I mean not the entire system, but  all the files that went with the respective *-desktop packages. 
IH[/QUOTE]

If you haven't installed them yet, use **aptitude** to install the meta-packages. Then to uninstall, just type [b]aptitude remove ubuntu-desktop[b], for instance.

---

### Post by ivanhelguera on 2006-02-12
[QUOTE=newuser111]if you install debfoster it will show you which meta package is keeping which packages installed[/QUOTE]

OK i used it looks like a valuable tool. Are there any known issues with the app?

> If you haven't installed them yet, use aptitude to install the meta-packages. Then to uninstall, just type [b]aptitude remove ubuntu-desktop[b], for instance.
Will that work if installed them via some other method (apt-get, if memory serves?)
Thanks a lot!
IH

---

### Post by aysiu on 2006-02-12
I wrote [a HowTo on uninstalling Kubuntu](http://www.ubuntuforums.org/showthread.php?t=96048) and [a HowTo on uninstalling Ubuntu](http://www.ubuntuforums.org/showthread.php?t=96046).

---

