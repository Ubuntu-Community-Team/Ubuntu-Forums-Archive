---
title: "Where is my VirtualBox OS?"
date: 2011-04-12
forum: General Help
---

### Post by GroogFish on 2011-04-12
I've just installed Windows XP in virtual box to use some windows software but I have no idea where VB put the OS. Where can I find this?

---

### Post by Vaphell on 2011-04-12
VB 3 puts virtual systems in ~/.VirtualBox and VB 4 in ~/VirtualBox VMs
when you run VB you click on listed XP's settings and there should be info where it's installed.

---

### Post by tgm4883 on 2011-04-12
> **GroogFish said:**
> I've just installed Windows XP in virtual box to use some windows software but I have no idea where VB put the OS. Where can I find this?

Not entirely sure what you mean.

If you want to know how to start it, open up Virtualbox and double click on the virtual machine.

If you are looking for it on the filesystem, it in in your home directory, under either 'VirtualBox VMs' or '.VirtualBox'. The second one is a hidden folder, and was used in VirtualBox version before version 4

---

