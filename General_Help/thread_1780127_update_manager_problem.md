---
title: "update manager problem"
date: 2011-06-11
forum: General Help
---

### Post by new7linux on 2011-06-11
hi:-
[SIZE=3]before 2 hour i install ubuntu 11.04 64 bit

but now i have this problem :-

[/SIZE]```
[SIZE=2]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/iq.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened[/SIZE].'
```

[SIZE=3]ubuntu software center does not has any program"it still searching"[/SIZE]
[SIZE=4]
how can i repair this problem??[/SIZE]

---

### Post by linuxinstalledfromhdd on 2011-06-11
sudo rm -vf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get upgrade

Make sure you are hardwared to the internet during the update process if possible.

---

### Post by new7linux on 2011-06-11
thank you the problem is repair, but why this problem occurred??

---

### Post by linuxinstalledfromhdd on 2011-06-11
Sometimes not letting updates finish correctly. Poor internet connection. Not sure.  

Here is a guide:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by new7linux on 2011-06-11
thanksss

---

### Post by linuxinstalledfromhdd on 2011-06-11
if you are done with help, please go up and click Thread Tools and mark this thread closed.. and you are very welcome.. :)

---

