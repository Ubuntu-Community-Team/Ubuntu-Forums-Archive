---
title: "Curly brackets in apt get results?"
date: 2010-11-19
forum: General Help
---

### Post by bogdarnet on 2010-11-19
Okay, I don't know if this is unusual, but I can't seem to find anything about it through online searching.  Are "procmail{u}" and "linux-headers-2.6.32-25-generic-pae{a}" normal results?  (See below for context.)

I'd just turned on the NX bit as detailed here:

[https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)

Then, to enable PAE, I used the apt get command from here:

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

"sudo aptitude install linux-generic-pae linux-headers-generic-pae"

What struck me as odd, because I hadn't seen these before, was the curly brackets (or flower brackets or braces) in the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  linux-generic-pae linux-headers-2.6.32-25-generic-pae{a} 
  linux-headers-generic-pae linux-image-2.6.32-25-generic-pae 
  linux-image-generic-pae 
The following packages will be REMOVED:
  procmail{u} 

Thanks in advance!

---

