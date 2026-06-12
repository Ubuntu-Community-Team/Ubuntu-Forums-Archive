---
title: "no harddisk on dapper"
date: 2006-04-19
forum: General Help
---

### Post by Ubimad on 2006-04-19
i am having serious problem wit the dapper ubuntu but i am not sure if it is kernel related. got a selfmade pc with a Asus K8N4-E Deluxe, nForce4 mainbord, 2 sata 80 gb harddisk identicaly the same ones.
on breezy i runs with software  raid1 fine. then with the dapper live-cd i see no harddisk, as well as no network hardware.
install with dappper comes up to the partitions part, where it stopps, and says no harddisk found.
so it upgraded breezy with the kernel 2.6.16 according to [this]("http://ubuntuforums.org/showthread.php?t=157560")
worked all fine, reboot with the new kernel, then it ends with:  /bin/sh: can't access tty: Job control turned off
have all raid and nv_sata build in kernel.

i need to try this hardware constalation on the kernel 2.6.16, since Xen 3.0 runs with this kernel version. 
i am just wondering what changed so dramatically that the latest kernels do not run on my machine. experience the same symptom on fedora 4 to fedora 5
guess it is kernel related, but still anyone out there who can help.

thank you:-|

---

