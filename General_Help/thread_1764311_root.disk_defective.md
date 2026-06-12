---
title: "root.disk defective"
date: 2011-05-21
forum: General Help
---

### Post by Thisisnotanid on 2011-05-21
Hi everyone!

        I am new to Ubuntu and Linux in general, and as is to be expected from such a disposition, have landed myself in trouble. I installed Ubuntu with WUBI and later created a new .disk file with larger capacity to accommodate the growing needs of my system. The new hard disk image has 11.04 on it (as does the old one), and it started shutting down unexpectedly a while back. Whenever I tried booting into that installation it took me to the grub command line. I tried many things to try to boot into the OS, but it always gave me some error along the lines of boot initrd missing (or some important boot realted file missing).


      Luckily, I had kept my previous .disk file containing an exact copy of the system when it was made. I renamed that to root.disk and it booted perfectly! Though it seemed that it was also going to suffer the same fate if I hadn't asked the system to repair broken packages and update grub-bootlader through safe mode. Everything's fine with the old disk image now, but I would really like to fix the new image I created or at the very least try to recover the new files I created on that image.

         Certain guides I've looked at provide very good solutions but require using the LiveCD, which I can't since for some reason when I try to it gives me the error message along the lines of "input output error, cannot mount loop0/dev/or something" Also, when I upgraded to 11.04, halevt didn't install properly giving the error message about sub-process exit status code 100. Now every time I install something with the terminal, it gives the same error message concerning halevt. I don't know if that helps or not.


Any help would be appreciated!

---

### Post by Thisisnotanid on 2011-05-22
Anyone?

---

