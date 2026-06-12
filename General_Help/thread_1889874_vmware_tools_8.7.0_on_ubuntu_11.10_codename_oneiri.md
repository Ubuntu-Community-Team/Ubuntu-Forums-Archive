---
title: "vmware tools 8.7.0 on ubuntu 11.10 codename oneiric"
date: 2011-12-02
forum: General Help
---

### Post by atosw on 2011-12-02
i have a VM(workstation7.1.5 build-491717) running ubuntu 11.10.

i'm trying to install vmware player on this ubuntu VM:

```
gksudo bash VMware-Player-4.0.1-528992.x86_64.bundle
```
but i get an error telling me to install version 8.7.0 of vmWare tools

My question is where can i find vmWare tools 8.7.0?

[IMG]http://i.stack.imgur.com/waIc2.jpg[/IMG]

---

### Post by carranty on 2011-12-02
Sorry, I know this doesn't answer your question but I have to ask, why do you want to install a virtual operating system inside of another virtual os?  You're going to start experiencing significant slow down of your virtual systems.

---

### Post by carranty on 2011-12-02
In answer to your question, the Vmware tools are part of the open-vm-tools package, try installing them first, then retry installing the bundle file
sudo apt-get install open-vm-tools

---

### Post by atosw on 2011-12-02
> **carranty said:**
> Sorry, I know this doesn't answer your question but I have to ask, why do you want to install a virtual operating system inside of another virtual os?  You're going to start experiencing significant slow down of your virtual systems.

i'm mounting a vm for a friend (who doesn't know **** about computer) who has ubuntu installed...yes i converted him to using ubuntu! but he still needs windows to run some games!!! damn gamers :)

---

### Post by carranty on 2011-12-02
Did installing open-vm-tools help?

> **atosw said:**
> i'm mounting a vm for a friend (who doesn't know  **** about computer) who has ubuntu installed...yes i converted him to  using ubuntu! but he still needs windows to run some games!!! damn  gamers :smile:

If I understand this correctly a virtual machine is not the way to go.  It sounds like your friend has Ubuntu installed as his operating system but he wants to be able to play windows games.  To do this he really needs to install both Ubuntu and Windows on the same machine, and choose which one to boot into at startup (this is known as dual-booting windows and ubuntu).  Virtual machines don't support 3d acceleration very well and so most modern games are not going to run very well within one.

I still don't understand why you need a virtual os within a virtual os.  What is the primary os, virtual os and virtual-virtual os?

---

