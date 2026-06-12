---
title: "synaptic can't find the glib"
date: 2006-05-09
forum: General Help
---

### Post by ozkan on 2006-05-09
i need glib for a program named Anjuta. But my Synaptic package manager can't find glib, it finds libglib which is already installed ?

---

### Post by Al3xanR0 on 2006-05-09
you may need to update your /etc/apt/sources.list go [here]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by disk11 on 2006-05-18
[QUOTE=ozkan]i need glib for a program named Anjuta. But my Synaptic package manager can't find glib, it finds libglib which is already installed ?[/QUOTE]

It's called libglib.

---

### Post by eddye00 on 2007-04-30
```
sudo apt-get install libglib1.2-dev
```

Results: 
```
checking for glib-config... /usr/bin/glib-config
checking for GLIB - version >= 1.2.2... yes
```

Ubuntu 7.04
;D

---

