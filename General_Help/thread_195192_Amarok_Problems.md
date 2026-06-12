---
title: "Amarok Problems"
date: 2006-06-12
forum: General Help
---

### Post by Vyizis on 2006-06-12
I am trying to get amarok running on my new install of ubuntu. I have installed amarok by doing the following

```
apt-get install amarok
```

But when i try this i get the following error message
```
dan@danslaptop:~$ sudo apt-get install libxine-extracodecs

Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

```

Is there another option?

---

### Post by ticool on 2006-06-12
add the multiverse and restricted repositorys to you source.list
Then try to install it agaiN!

---

### Post by barbarian on 2006-06-12
hei, and don't forget *sudo apt-get update *after activating extra repos:)

---

### Post by Vyizis on 2006-06-12
I have un commented all of the lines in the sources.list file, that was the first thing i did after first installing ubuntu so i could get ndiswrapper and all of the updates.

---

### Post by Vyizis on 2006-06-12
Ok i got it now thanks

---

### Post by matrooswolf on 2006-06-12
Try here for the latest version:
[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

---

