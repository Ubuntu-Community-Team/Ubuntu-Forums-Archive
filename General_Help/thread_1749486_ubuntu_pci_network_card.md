---
title: "ubuntu pci network card"
date: 2011-05-04
forum: General Help
---

### Post by driftlife on 2011-05-04
Ubuntu Server. After installing I noticed it had no onboard nic. (Genius! But it is just a test machine.) Threw in a PCI card. No idea if its compatible, ran lspci -v and got this:
 
Flags: medium devsel
I/O Ports at <unassigned> [disabled]
 
Suggestions?

---

### Post by sostentado on 2011-05-04
Have you tried updating the system?

---

### Post by driftlife on 2011-05-04
Thats funny.  Even better, I went over to the machine and tried to run updates...
 
The PCI card I'm trying to get working is the only NIC on the machine.
Thought maybe there was a command to configure it or something?
Assign the pci device to eht0 or something?

---

