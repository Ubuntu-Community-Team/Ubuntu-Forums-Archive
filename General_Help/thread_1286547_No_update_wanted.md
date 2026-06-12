---
title: "No update wanted"
date: 2009-10-09
forum: General Help
---

### Post by col48 on 2009-10-09
This refers to VirtualBox, but it could be any application.

I installed VirtualBox 2.0 on my machine using Synaptic many months ago.  Subsequently I upgraded to 2.1 as part of one of the fortnightly updates.  

No problem.

Later, Synaptic offered v2.2 but this failed to install a couple of times (separated by several weeks), so I have been unticking it in the list of updates each couple of weeks and ignoring the 9(!)-pointed orange star in the panel in between times.  Version 2.1 has been fine.

This week, when I fired up the VM, VirtualBox (not Synaptic) gave me a link to install v3.0 and I thought I'd give it a go, so I did the install from there and it worked fine - both the install and the VM running under VirtualBox.

However, when I look at the available package list, Synaptic seems to think I still have v2.1 installed and wants to offer me v2.2.

How do I let Synaptic in on the secret?  I am unwilling to uninstall VirtualBox 3.0 and reinstall, as it is not broken.

---

### Post by MelDJ on 2009-10-09
remove the sun repository from your sources list

---

### Post by col48 on 2009-10-09
Thanks.  I'll try that.

---

### Post by slakkie on 2009-10-09
You could also look into pinning packages.

Google: apt pinning

---

