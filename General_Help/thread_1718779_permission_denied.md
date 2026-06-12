---
title: "permission denied"
date: 2011-03-31
forum: General Help
---

### Post by dabyv on 2011-03-31
hi all
why when i want to install some thing on my ubuntu 10.10 from terminal
or user any other commands i have this out pot
permission denied
this one i want to install make-3.82
i extract files and open install file (a text guide file)
in this guide i see this

[HTML]
The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.
[/HTML]

i do this i open my terminal cd to that location and type ./configure

and outpot is this:
bash: ./configure: Permission denied

when i want to make any softwares i have the same problem?
i have to give terminall any permission or something?
i want to do any action to dont see this .... message again

---

### Post by fela on 2011-03-31
```
chmod +x ./configure && ./configure
```

But you're installing in the wrong way. Install from synaptic or using apt-get.

---

### Post by dabyv on 2011-04-01
> **fela said:**
> ```
chmod +x ./configure && ./configure
```

But you're installing in the wrong way. Install from synaptic or using apt-get.
if i use this code i dont see this message again?

---

### Post by d3v1150m471c on 2011-04-01
you have a debian based system, ie ubuntu. when you go installing source code, which isn't necessarily a bad thing, it can become disorganized in a hurry. synaptic and apt-get allow you to install easier and effectively manage what's on your computer. and when it's uninstalled, it's actually uninstalled, not left for you to find and clean up. always try to use a .deb if you can find one oppossed to installing from source. 

```

sudo apt-get install <program>

```

---

### Post by suryaworldedu on 2011-04-01
I also faced the same problem. can anyone help me out please?

---

### Post by rnerwein on 2011-04-01
hi
try: sudo ./configure 
in the directory which contains your configure file.
ciao

---

### Post by fela on 2011-04-01
You're trying to install source code, however almost all packages can be found from the repositories.

Instead of downloading software off random pages on the net, the 'Linux way' is to use the package manager. So in Ubuntu, you could search for your package in the software centre, or synaptic, or you can install it like this:

```
sudo apt-get install packagename
```

---

