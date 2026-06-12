---
title: "manually removing a package"
date: 2009-09-11
forum: General Help
---

### Post by usien on 2009-09-11
is there a way of manually removing a package from my system, without using a deb or a package manager?

---

### Post by Claus7 on 2009-09-11
Hello,

this is a quick one: find the folders where this package is installed and wipe them out, all of them!
Have in mind though, that if this particular package is needed from others, then you should cause breakage of your system. So beware!

Also you might have to be root in order to be able to remove some of the folders of the package. 

Regards!

---

### Post by wojox on 2009-09-11
Use:

```
sudo apt-get --purge remove <package>
```

---

### Post by usien on 2009-09-11
this is the output

sudo apt-get --purge remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by akakingess on 2009-09-11
Can you not just do a "sudo apt-get install non-free adobe-flashplugin" within the terminal?

---

