---
title: "GRUB Question?"
date: 2011-12-13
forum: General Help
---

### Post by QuantumMonkey on 2011-12-13
Hey, yesterday I attempted to uninstall Fedora from my system, as it didn't work and I never used it. I was stupid and removed the partition but never got the Windows bootloader back.

Will installing Ubuntu alongside my Windows 7:

a) Fill up the free space left by Fedora, the installer wouldn't let me choose it as it has no filesystem name or something, and

b) Make me able to start Windows from the GRUB menu.

Thanks.

---

### Post by BC59 on 2011-12-13
Depends on how you have partitioned your HDD.
In any case during installation, clicking "Something Other" you get Gparted and you can arrange your partitions. Delete Fedora's partition and instead install Ubuntu. The Grub is going automatically to recognize Ubuntu and Windows.

---

### Post by Mark Phelps on 2011-12-13
If the space is actually empty now, I don't believe there is a "Use largest free space" option in the installer anymore; so instead, you have to do manual partitioning.

Be very careful to NOT choose the partition containing Win7; otherwise, it will be erased in the process.

Also, while it SHOULD present a GRUB menu when finished, if it does not and boots directly into Ubuntu, that is easily fixed by opening a terminal and entering "sudo update-grub".

---

