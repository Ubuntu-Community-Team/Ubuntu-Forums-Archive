---
title: "Run Windows on Ubuntu (already have dual-boot)"
date: 2009-12-24
forum: General Help
---

### Post by Frogging101 on 2009-12-24
I have an existing Windows installation on another partition. Ubuntu is great, but I cannot play games on it that were designed for Windows. The only way to do it is rebooting. Is there a way I can use that Windows install, and run it 'inside' ubuntu? That way I have all the DLLs and stuff.

What is the optimal solution to my problem?

---

### Post by switch10 on 2009-12-24
you can use Wine, or install windows in a virtual machine like VirtualBox

good luck

---

### Post by linux4life88 on 2009-12-24
The only way that I know of to run Windows inside of Ubuntu is a virtual machine. The problem is that some games do not like to be played inside of virtual machines. You could download Virtualbox and give it a try. This is the only way that I know of to accomplish what you are wanting to do.

---

### Post by 3Miro on 2009-12-24
For newer 3D games, you want to use wine (not all games run however and they have to be specifically installed inside Ubuntu). For general applications, Virtual Box is probably the best. Newer versions of Virtual box support directx, but it is still somewhat experimental and I don't think it can run the latest shooters.

---

### Post by Frogging101 on 2009-12-24
How would I set it up to use my existing Windows 7 install? It is on a different partition.

---

### Post by bayusetiaji on 2009-12-24
I'm using VirtualBox on Ubuntu, and I can run many OSes within it.
If I want to run windows program from Ubuntu directly, I use Wine..
All run well

---

### Post by bodhi.zazen on 2009-12-24
> **Frogging101 said:**
> How would I set it up to use my existing Windows 7 install? It is on a different partition.

Running an existing Windows install on a Virtual machine is not trivial, and requires configuring Windows to do so as you windows install will complain that the "hardware" has changed.

It is far easier to re-install windows and use a virtual hard drive.

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

Note, the advice to create a "hardware profile", do you know how to do that ?

---

