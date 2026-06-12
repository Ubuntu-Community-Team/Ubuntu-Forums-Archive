---
title: "I need help nstalling a pkg1.run file"
date: 2009-10-13
forum: General Help
---

### Post by Romanrp on 2009-10-13
I have downloaded the NVIDIA-Linux-x86-185.18.31-pkg1.run file.
Now I need to install it but I have trouble doing so.
I looked at other threads but it didn't help me.
Any help?

---

### Post by Arup on 2009-10-13
First of all you need run2.Then do a sudo apt-get install build-essential

Then go to Synaptic and remove linux restricted modules and linux restricted modules common, do a ctrl+alt+F2 and login
 
Do a sudo /etc/init.d/gdm stop and then do a sudo sh NVIDIAxxxxxxxxx

Make sure nvidia driver is in HOME folder.

---

### Post by Romanrp on 2009-10-13
Thanks for your help,fixed it myself.
Now I need to activate compiz.

---

