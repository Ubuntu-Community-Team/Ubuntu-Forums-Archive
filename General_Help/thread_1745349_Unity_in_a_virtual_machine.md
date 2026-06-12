---
title: "Unity in a virtual machine"
date: 2011-04-30
forum: General Help
---

### Post by salmontres on 2011-04-30
Hi guys,

Has anyone gotten Unity to work using VirtualBox? I upgraded from 10.10 just fine, and I can get Ubuntu 11.04 to run on my virtual machine in Windows, but I can't get the great looking Unity graphics displayed. It claims one of the requirements isn't met, but I've given it plenty of video memory (128MB), plenty of RAM(2GB), and two cores to run. Could it be a glitch in the virtual environment? (Also, I can get Unity to run on the same computer when I don't run through a virtual machine, but unfortunately I need Windows for this university project :(

---

### Post by cymbaline42 on 2011-05-01
I got Natty with Unity to run on Virtualbox running inside Ubuntu 10.10 32 bit.  I had given the Natty VM 1GB of RAM, ~100 MB of video memory, and one out of my two processors.

A few suggestions: 


[LIST=1]
[*]Use the latest version of Virtualbox (4. something).
[*]Enabled 3D acceleration in the Display settings of the VM in Virtualbox.
[*]Install Guest Additions.
[/LIST]

---

### Post by salmontres on 2011-05-01
Agh! I forgot to upgrade Guest Additions. That did it!


Thanks Cymbaline!

---

