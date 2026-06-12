---
title: "Synaptic and Apt-Get"
date: 2006-04-25
forum: General Help
---

### Post by matt1988 on 2006-04-25
I have been having problems with synaptic and ap-get.  When I try to open synaptic it just closes. When I try to use apt-get it gives me
 > Segmentation faulty tree... 50%
 
I have found the fix for this.
> sudo rm /var/cache/apt/*.bin

However, I need to use this command everytime I try to use syanptic or apt-get. Is there anyway I can fix whatever I did to screw up?

---

### Post by dg_w on 2006-04-25
This may help you out:


I suspect corrupted data files. Delete
 /var/cache/apt/*.bin followed by "apt-get update" to reset apt.

cd /var/cache/apt
sudo rm *.bin
sudo apt-get update

---

