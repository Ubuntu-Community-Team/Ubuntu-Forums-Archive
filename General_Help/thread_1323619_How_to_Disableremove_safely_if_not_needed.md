---
title: "How to Disable/remove safely if not needed"
date: 2009-11-11
forum: General Help
---

### Post by Flywaver on 2009-11-11
I am wondering how we can safemy remove CUPS as I have absolutely no use for it and I want System Update to offer me updates for it! 

If I try to remove CUPS in Synaptic it wants to remove ubuntu-desktop, which is crucial...why is that? 

Is CUPS taking some memory even if it's not needed?

Thanks in advance?

---

### Post by mikewhatever on 2009-11-12
In fact, ubuntu-desktop is not a crucial package at all and can be safely removed. If unsure, run a simulation from Terminal and post the output, for example:

```
sudo apt-get -s purge cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgutenprint2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bluez-cups* cups* cups-driver-gutenprint* foomatic-db-hpijs* hal-cups-utils* hpijs* hplip* splix*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Purg bluez-cups [4.32-0ubuntu4.1]
Purg splix [2.0.0-0.1ubuntu3.1]
Purg foomatic-db-hpijs [20090218-0ubuntu3]
Purg hpijs [3.9.2-3ubuntu4]
Purg hplip [3.9.2-3ubuntu4]
Purg hal-cups-utils [0.6.19+git20090217-0ubuntu7]
Purg cups-driver-gutenprint [5.2.3-0ubuntu5]
Purg cups [1.3.9-17ubuntu3.4]

```

The -s flag after apt-get means the command is a simulation, and nothing is actually removed.

---

### Post by Flywaver on 2009-11-12
Wow thanks a LOT! Ran the simulation and nothing happened so I guess I can safely remove CUPS! :)

Cheers!

---

### Post by jollysnowman on 2009-11-12
I, in addition to this, went into the Synaptic manager and removed all packages with cups in the name, except for two, libcups1somethingorother and otherlibcups, that almost all my applications depend on.

---

### Post by Flywaver on 2009-11-12
> **jollysnowman said:**
> I, in addition to this, went into the Synaptic manager and removed all packages with cups in the name, except for two, libcups1somethingorother and otherlibcups, that almost all my applications depend on.

I removed everything CUPS related...so far no problem at all! :)

---

