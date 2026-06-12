---
title: "Uninstall An Application"
date: 2011-06-06
forum: General Help
---

### Post by Gebriel on 2011-06-06
I want to install an application on ubuntu 11.04 but it is saying the package need to be reinstalled to uninstall, when I try to reinstall it it wont let me, all it say is ```
Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

```
is there a way to remove it ?

---

### Post by ChrisKu on 2011-06-06
Try starting Synaptic and deselect the package you want to remove.

---

### Post by Elfy on 2011-06-06
Try 
```
sudo apt-get install -f
sudo dpkg --configure -a
```

If that doesn't help, try 
```

sudo dpkg --purge --force-all *packagename*
```

or this if that fails to help 

```
sudo dpkg --remove --force-remove-reinstreq *packagename*
```

Change packagename to whatever you need.

---

### Post by Gebriel on 2011-06-06
I tried all but I always get 
```
E: The package bochs needs to be reinstalled, but I can't find an archive for it.

```

what shall I do?

---

### Post by Gebriel on 2011-06-07
please anybody? The application I am trying to install is Bochs and it is giving me a hard time...

---

### Post by nzjethro on 2011-06-07
yeah, you'll have to purge it. Try
```
sudo dpkg --purge bochs
```

---

