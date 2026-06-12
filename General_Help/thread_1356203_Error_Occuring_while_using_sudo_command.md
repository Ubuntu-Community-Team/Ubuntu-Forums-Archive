---
title: "Error Occuring while using sudo command"
date: 2009-12-15
forum: General Help
---

### Post by Madasamy on 2009-12-15
While Using Sudo command as below, the following error has occured in the Command prompt. 
Its not only occuring for this, but for all the commands related to installation like this or apt-get , i am getting  this error. Please someone give me a way to solve.

Error Message :

madasamy@madasamy-desktop:~$ sudo aptitude purge rhythmbox
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Thanks 
Madasamy

---

### Post by collinp on 2009-12-15
Hmm. Try running:
```
sudo killall aptitude
sudo killall apt-get
```

and see if that fixes your problem.

If it does, then you had instances of apt-get or aptitude already running and, when you do, the administration directory is locked to that one instance.

---

### Post by boomslang20117 on 2009-12-15
i've got the same problem too when i try to install gobject-introspection-repository. it says that my gnome shell is broken. 

E: /var/cache/apt/archives/gobject-introspection-repository_0.6.5-0ubuntu1_i386.deb: trying to overwrite '/usr/share/gir-1.0/JSCore-1.0.gir', which is also in package libwebkit-dev 0

---

### Post by boomslang20117 on 2009-12-15
anyway i discover what's the cause of the problem. it is gnome shell itself. it seems that after i removed it other sudo apt-get install works perfectly well. but in the end of the day i still need gnome shell don't i?

---

