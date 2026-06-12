---
title: "Update Manager is showing error"
date: 2011-05-11
forum: General Help
---

### Post by neiu bee on 2011-05-11
Hi, i hav recently upgraded to 10.10 and followed by wine. I tried to upgrade from wine 1.2 to 1.3 but i could not. Later i encountered a problem. This is it:

An unresolvable problem occurred while initializing the package information.
 
"E : ntu-wine/ppa/ubuntu is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list'"

---

### Post by ~Plue on 2011-05-11
Post the contents of the file so that we could take a look at it; (run from a terminal window)
```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```

---

### Post by demilord on 2011-05-11
or try from terminal,   sudo apt-get update  .. if it finds a error in the source list it will ask you to do it again afterwards

---

### Post by garvinrick4 on 2011-05-11
Something wrong with ppa for wine in your sources.list.
delete it or comment it out.
```
sudo gedit /etc/apt/sources.list
```hit save when done deleting or commenting out (a # in front of offending line)
```
sudo apt-get update
```Above to update sources list:
Now reinstall your ppa

---

