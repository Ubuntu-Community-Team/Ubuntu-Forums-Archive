---
title: "How can I remove 2GB virtual drive created with qemu"
date: 2010-01-23
forum: General Help
---

### Post by O-pos on 2010-01-23
Hello,

I installed Windows XP on my system using QEMU as a 2GB virtual drive in my home directory. I don't want to have it anymore, however I can't get rid of this 2GB used space with windows XP. I can't even delete QEMU, because the command sudo apt-get remove qemu tells me that package qemu is not installed. (however it is there, works, and is able to start Windows XP as usual). 

How can I get rid of this qemu/Win XP and have 2GB of my home folder available again?

---

### Post by jamesisin on 2010-01-23
Two things...

First, by what method did you install this qemu?  (Check in Synaptic to see if qemu is marked as installed.  You can also try 'which qemu' from the command line.)

Second, you ought to be able to merely delete the file which represents the VM to free up the space alloted for that machine.  Since qemu doesn't appear to be virtualization technology (rather just a processor emulator), which application did you use to create your VM?

---

