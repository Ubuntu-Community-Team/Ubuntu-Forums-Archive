---
title: "are there any nice Synaptic alternatives? that dont use 100mb ram"
date: 2006-04-21
forum: General Help
---

### Post by cosmoshell on 2006-04-21
are there any nice Synaptic alternatives? that dont use 100mb ram

---

### Post by lcg on 2006-04-21
[QUOTE=cosmoshell]are there any nice Synaptic alternatives? that dont use 100mb ram[/QUOTE]
Fire up your favourite terminal application and
```
sudo aptitude
```

HTH,
Lars

---

### Post by yoink23 on 2006-04-21
Using apt-get update or upgrade or dist-upgrade or install, etc is one alternative...

---

### Post by cosmoshell on 2006-04-21
i think ill start useing aptitude. but it would be nice to have a gui.

---

### Post by harisund on 2006-04-21
I agree. Synaptic is just "too big" to my likings. 

I use a combination of aptitude and apt-cache to search for packages that I want. Both "aptitude search" and "apt-cache search" return nice package listing, and "dpkg --list" used with "grep" allows me to filter through installed packages. 

But having a GUI can be handy. Maybe instead of having a single application handle everything including sources listing, upgrading/dist-upgrading, automatic updates etc.. we can have GUI applications that do just one thing. For example, one software to assist in modifying, deleting and adding repositories, one application like Windows's Add/Remove programs, but only for uninstalling existing packages, one for searching and adding applications. 

This way, even though we will have multiple programs, atleast each one will not be bloated, and instead use lesser memory.

---

### Post by _linux_ on 2006-04-21
There is the Smart Package Manager.

---

