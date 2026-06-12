---
title: "How to uninstall"
date: 2009-07-05
forum: General Help
---

### Post by -Oz- on 2009-07-05
Hey everyone...
Am new to ubuntu and linux thing....recently i installed Freeciv on my ubuntu 9.04...and didn't really liked it that much. How do i remove it from the system???
Its not listed in Add/remove....any help would be really appreciated.

---

### Post by DeMus on 2009-07-05
> **-Oz- said:**
> Hey everyone...
Am new to ubuntu and linux thing....recently i installed Freeciv on my ubuntu 9.04...and didn't really liked it that much. How do i remove it from the system???
Its not listed in Add/remove....any help would be really appreciated.

How did you install it?

---

### Post by credobyte on 2009-07-05
Source : [http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
```
sudo dpkg -r package_name
```

---

### Post by -Oz- on 2009-07-05
"sudo dpkg -r " doesnt work

I downloaded the source files....and used the following commands

./configure

make

sudo make install

---

### Post by wojox on 2009-07-05
You try

```
sudo apt-get remove Freeciv
```

or however you spell it

---

### Post by -Oz- on 2009-07-05
Nope that isn't working either....

sudo apt-get remove freeciv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package freeciv

Sorry for being soo n00b :S

---

### Post by credobyte on 2009-07-05
This should work : [http://lists.arabeyes.org/archives/general/2002/June/msg00041.html](http://lists.arabeyes.org/archives/general/2002/June/msg00041.html)

---

### Post by -Oz- on 2009-07-05
Heeehawww....thanks credo.... :D

---

