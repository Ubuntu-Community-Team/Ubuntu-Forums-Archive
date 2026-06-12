---
title: "Updating everything all at once (packets, etc.)"
date: 2010-11-12
forum: General Help
---

### Post by moo9801 on 2010-11-12
Just wondering if there is a way to update all of my packets on Ubuntu server 10.10 all at once.

Thanks in advance to all,
OSX

---

### Post by 3Miro on 2010-11-12
What do you mean? Do you mean reinstall everything? Updates apply only packets that are newer than the ones that you have installed.

---

### Post by moo9801 on 2010-11-12
I mean like if package2 is version 1.0 on my server,and the newest released version is 3.0, i want to update that one and all the rest to their current version.

---

### Post by 3Miro on 2010-11-12
You can go to System -> Admin -> Update Manager or you can go to the Terminal (Apps -> Accessories -> Terminal) and type:

```
 sudo apt-get update 
sudo apt-get upgrade
```

The first reloads the list of available packages and the second upgrades all of the available packages.

---

### Post by moo9801 on 2010-11-14
Thanks man.

---

