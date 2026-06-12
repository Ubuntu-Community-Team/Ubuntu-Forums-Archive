---
title: "Amarok"
date: 2009-09-26
forum: General Help
---

### Post by arnab_das on 2009-09-26
I downloaded and installed amarok after hearing a lot about it. The file size was enormous when compared to other Ubuntu apps, anyway the thing is, I didnt like it at all. So, I removed it from the Synaptic so that I could do the "complete removal" thingy. However the amount of space which was there on my hard drive has been reduced even after the complete removal of amarok.

how can i remove these files which havent been removed yet?

---

### Post by Woody1987 on 2009-09-26
try sudo apt-get autoremove to remove any unnecessary dependencies that were installed with amarok.

---

### Post by arnab_das on 2009-09-26
> **Woody1987 said:**
> try sudo apt-get autoremove to remove any unnecessary dependencies that were installed with amarok.

brilliant that was awesome! "sudo apt-get autoremove" freed 114MB!!! thanks a lot! :)

btw can i use this command regularly in order to free up some space?

---

