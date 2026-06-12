---
title: "Somehow killed my plymouth startup splash"
date: 2011-05-22
forum: General Help
---

### Post by dwasifar on 2011-05-22
Fooling around with trying to edit splash themes, and in trying to apply one, I broke the startup splash.  The shutdown splash still works.

I know that update-initramfs -u is supposed to fix this, but it hasn't.  I run dpkg-reconfigure plymouth, and it gives me the list of themes; I can pick one, and it seems to do its thing; I run update-initramfs -u, and that looks like it worked too; but then I reboot, and the shutdown splash is unchanged, and the startup splash is just a black screen until GDM loads.  It's as if I hadn't changed anything.  

Anyone?

---

### Post by dcstar on 2011-05-23
> **dwasifar said:**
> Fooling around with trying to edit splash themes, and in trying to apply one, I broke the startup splash.  The shutdown splash still works.

I know that update-initramfs -u is supposed to fix this, but it hasn't.  I run dpkg-reconfigure plymouth, and it gives me the list of themes; I can pick one, and it seems to do its thing; I run update-initramfs -u, and that looks like it worked too; but then I reboot, and the shutdown splash is unchanged, and the startup splash is just a black screen until GDM loads.  It's as if I hadn't changed anything.  

Anyone?

Install the **galternatives** package and look in the relevant section there.

---

