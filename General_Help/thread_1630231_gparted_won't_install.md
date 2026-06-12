---
title: "gparted won't install"
date: 2010-11-24
forum: General Help
---

### Post by bradhaack on 2010-11-24
ubuntu 10.10
I wanted to run gparted to repartition a drive.

sudo apt-get install gparted

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gparted: Depends: libparted0 (>= 2.2-1) but it is not going to be installed
E: Broken packages

---

### Post by Quackers on 2010-11-24
If you go into Synaptic Package Manager are there any broken packages listed at the bottom left of the screen?

---

### Post by bradhaack on 2010-11-24
Nope, 0 broken

---

### Post by Quackers on 2010-11-24
Hmm. Try installing through synaptic and see if its dependencies are picked up alright.

---

