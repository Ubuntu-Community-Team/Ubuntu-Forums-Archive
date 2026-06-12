---
title: "Safe Way to Clean Up /lib?"
date: 2011-01-03
forum: General Help
---

### Post by klausner on 2011-01-03
Is there a safe way to cleanup the /lib file tree? Mines gotten too large for the filesystem it's on (/), and I've already shot myself in the foot a few times trying to delete things.

---

### Post by AlphaLexman on 2011-01-03
You really shouldn't be deleting or removing files at random from /lib. It is an important system directory that makes your linux machine work properly.

What exactly are you trying to 'clean-up'?

---

### Post by klausner on 2011-01-03
> **AlphaLexman said:**
> You really shouldn't be deleting or removing files at random from /lib. It is an important system directory that makes your linux machine work properly.

What exactly are you trying to 'clean-up'?

I don't want to "randomly" delete files. That's why I asked if there was a "safe" method.

I'm trying to do exactly what I said in the original post. Reduce the space used by /lib. And no, I don't want to play games by moving files elsewhere and then linking them back to the original location.

---

### Post by WorMzy on 2011-01-03
The "safe way" would be to remove/purge unwanted applications through apt-get/synaptic/software centre.

```
sudo apt-get autoremove
```

should remove any unneeded packages which were installed to satisfy dependencies for applications you no longer have installed.

---

### Post by hawkmage on 2011-01-03
If you can be absolutely sure of all of the executables you and your system runs you can use the ldd command to figure out what libraries each executable uses and delete the rest.  This would somewhat of a recusive process since the individual libs may load other libs.  

This is not what I wold call a "Safe Procedure".  Make one mistake and your system can become be nonfunctional.  

Is you "/lib" on its own volume?  If not you should look to other directories on the volume to clean up.

---

### Post by hawkmage on 2011-01-03
> **WorMzy said:**
> The "safe way" would be to remove/purge unwanted applications through apt-get/synaptic/software centre.

```
sudo apt-get autoremove
```should remove any unneeded packages which were installed to satisfy dependencies for applications you no longer have installed.
Yes that would work if all applications and/or packages were installed through standard packages.  Any applications that have been insstalled by just using untar or a config/make/install from a tarball will likely not be in the apt-get database.

---

### Post by bodhi.zazen on 2011-01-03
It is far easier to perform a minimal install and add only those applications you wish to remove then remove "bloat" from a standard Ubuntu installation.

In general use the package management tools (apt-get, aptitude, synaptic, etc) to remove applications and do not remove things you do not understand.

---

### Post by klausner on 2011-01-03
> **WorMzy said:**
> The "safe way" would be to remove/purge unwanted applications through apt-get/synaptic/software centre.

```
sudo apt-get autoremove
```

should remove any unneeded packages which were installed to satisfy dependencies for applications you no longer have installed.

Ran that. Also "apt-get clean". Also "remove orphaned packaged". Also "bleachbit". Still think there is a significant amount of cruft.

---

