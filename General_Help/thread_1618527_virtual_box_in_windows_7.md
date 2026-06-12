---
title: "virtual box in windows 7"
date: 2010-11-10
forum: General Help
---

### Post by skyjacker on 2010-11-10
I got a new laptop with windows 7 installed, but I already miss ubuntu. I would like to set up Ubuntu in virtual box, but do not know the requirements ( how much ram, etc.. Are these listed anywhere?? Can someone help me out?
I have 3 gb of ram installed in my machine, with a 250 gb hd.

---

### Post by lmarmisa on 2010-11-10
No problem about the requirements. Your computer is perfect for running VirtualBox.

These parameters could be useful for defining a virtual machine for Ubuntu:

[LIST]
[*]Memory: 512-1024 Mbytes.
[*]Virtual disk: 10-20 Gbytes dynamically expanding storage.
[*]Network: NAT or better Bridged adapter.
[*]You do not need to use a physical CD for the Ubuntu installation. I prefer to select the Ubuntu iso file in the CD/DVD virtual device.
[*]Don't forget to install the Guest Addition in the Ubuntu guest system.
[/LIST]

---

### Post by P4man on 2010-11-10
Basically you just add up the requirements for either OS because you will be running and installing both. For most apps 1GB is enough for ubuntu, leaving windows with 2GB (when running the VM), which also works rather well. Should be fine.

---

