---
title: "Lightweight environment needed, but would still like Gnome from time to time."
date: 2010-11-14
forum: General Help
---

### Post by stratman4300 on 2010-11-14
Long time linux user here, but I've never had this need, so it's more of a question than anything else. 

I run VMware workstation and run several VMs on my laptop from time to time, so there are times that I need to conserve as much physical memory as possible. 

Currently I'm running Lubuntu for it's lightweight footprint, but I don't find it as functional as what I'm used to. (usually run gnome).

My question is mainly about libraries loaded at boot time. I'll admit I don't really know how shared libs work in linux. Are only the libs that are needed loaded into memory? 

I ask because what I'm thinking is using a full blown gnome desktop when i'm not in need of running my VMs, but switching to either fluxbox or LXDE when I do need to. 

Will I still get the full memory savings when I run one of the lighter weight window managers even though I have a full Gnome install on the system?

Sorry if it's a noobish question! :P

---

### Post by blueridgedog on 2010-11-14
Shared libs are linked to binaries and are called when needed.  If you don't run an application that calls a given library, you will not load it.  You should be able to install gnome desktop and select it when logging in (if using gdm) and have a choice of desktop environments.

---

### Post by stratman4300 on 2010-11-14
That's what I figured, just wanted verification prior to installing ubuntu-desktop. 

Thanks!

---

