---
title: "Different versions?"
date: 2009-09-19
forum: General Help
---

### Post by tranzue on 2009-09-19
Hello all,

I recently downloaded some recommended updates for Ubuntu Jaunty Jackalope.  After completed, I restarded my computer, and noticed my menu had two extra choices that looked like this:

2.6.28-15 Generic
2.6.28-15 Recovery

2.6.28-11 Generic
2.6.28-11 Recovery

Other Operating SYstems

Windows Vista (loader)

I'm assuming that the -15 means it is the updated version, but how can I get rid of the -11 from the menu?

Any help is greatly appreciated

---

### Post by marcopolo1981 on 2009-09-19
Open synaptic package manager
Run a serch for "linux-image-generic"
Select the older one/s for removal.
Click apply.

It is worth noting that it is sometimes beneficial to have multiple kernels installed, just in case something goes wrong. It is much easier to back-track should you have to. Also, they only take up a very small amount of your hard disk.

Mark

---

### Post by amauk on 2009-09-19
files for each kernel version you have only take up ~10mb in /boot

---

### Post by tranzue on 2009-09-19
Well I thank you both very much.  Maybe I should just keep it.

---

### Post by jerrrys on 2009-09-19
an easy way to manage kernels is **startup-manager**.  its located in synaptic package manager

---

