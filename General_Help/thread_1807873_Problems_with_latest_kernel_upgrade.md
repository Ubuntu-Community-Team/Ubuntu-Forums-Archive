---
title: "Problems with latest kernel upgrade"
date: 2011-07-19
forum: General Help
---

### Post by cptrohn on 2011-07-19
Laptop won't even boot into the newest kernel for 10.10... I can do a hard reboot and then I can choose from kernel versions and boot into the prior kernel... anyway I can remove the newest kernel or is there a know bug in some hardware?  I have an older laptop that is having the issue that has an AMD Sempron processor....

---

### Post by Joris Donders on 2011-07-19
Press the shift key directly after the bootsplash; this opens Grub. 

Select the previous kernel (the one that worked) and boot in the system. 

Once inside the system, open Synaptic and remove the newest kernel. 

Do in the terminal ```
sudo update-grub
```, and you're done. 

Maybe it was just a corrupt download; so try the update again.

---

### Post by ajgreeny on 2011-07-19
If you try to install it again you will first need to remove the kernel package from /var/cache/apt/archives, or it will be used again, and if it is corrupt, you will have the same problem.

---

### Post by cptrohn on 2011-07-19
Thanks Joris, I am having finding the kernel in synaptic, is there anyway to remove it via command line?

---

