---
title: "Dual Booting with Win7"
date: 2011-09-14
forum: General Help
---

### Post by Tbone07 on 2011-09-14
Hey guys im fairly new to the Ubuntu/Linux world. I've got Ubuntu 10.10 dual-booted with Windows7 and it works...kinda. For some reason i have both the GNU Grub boot screen appearing, and then if i select the Windows7 OS, it goes straight to the Windows Boot Manager screen. Is it possible to use only one of the two boot managers? I don't really care which one, its just going through 2 separate boot screens is getting annoying. Thanks

---

### Post by Rubi1200 on 2011-09-16
Hi and welcome to the forums :-)

Is this a regular or Wubi install?

Thanks.

---

### Post by Mark Phelps on 2011-09-16
> **Tbone07 said:**
> ... if i select the Windows7 OS, it goes straight to the Windows Boot Manager screen. Is it possible to use only one of the two boot managers? I don't really care which one, its just going through 2 separate boot screens is getting annoying. Thanks

When you see the Windows boot manager screen, are you again offered choices that include Ubuntu? OR does it only offer you MS Windows choices?

If it only offers you MS WIndows choices, that is how the Windows boot manager works.  The only way, in that case, to eliminate the GRUB manager would be to remove GRUB from the MBR, replace it with the Win7 MBR, and install something in MS Windows like EasyBCD -- and add Ubuntu to THAT.

---

