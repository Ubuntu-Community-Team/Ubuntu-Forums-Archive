---
title: "How to lock packages under /var/cache/apt/archives/ ?"
date: 2009-08-08
forum: General Help
---

### Post by ysha4171 on 2009-08-08
This is probably a newbie question:  i have used **apt-ge**t install for installing the software. And the packages are downloaded in **/var/cache/apt/archives**   directory.    ** Apt-get clean** will clean all the packages under /var/cache/apt/archives directory,    how can i lock the packages that i want to keep, so **apt-get clean** will bypass those locked packages?   Please tell me the command for this.:confused:

---

### Post by drs305 on 2009-08-08
ysha4171,

Welcome to Ubuntu and the Ubuntu forums.

I don't know of a command within the APT 'family' that will do this. You could always copy the packages you are interested in to another location. Remember too that these packages aren't needed once the application is installed - they can be removed without any adverse affect. The downside would be if you had a very slow connection or were concerned with download totals.

The 'lock' feature generally associated with packages is meant to prevent packages from being updated. 

This is achieved in Synaptic via Package, Lock Version or in apt-get with "echo 'packagename hold' | dpkg --set-selections" or "aptitude hold packagename"

---

### Post by ysha4171 on 2009-08-08
Ok. i get it!   Thanks very much for your help.  I love this forum!!!:P

---

