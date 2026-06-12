---
title: "grub entries on Lenovo ideapad"
date: 2010-07-11
forum: General Help
---

### Post by audiomick on 2010-07-11
Hallo.
I have a dual boot with UNR and Win7 on a Lenovo ideapad. The Grub menu lists a Win7 loader and a Vista loader. I assume the Vista loader refers to the recovery partition of the original (win7) install.

Does anyone know if this is true, or if not, what the entry refers to?

Incidentally, Ubuntu runs really nicely on this machine.

thanks.

---

### Post by mike555 on 2010-07-11
I think the one listed as vista is your restore partition ... by the way if you use it ,it will mess up booting Ubuntu till you reinstall grub ..

---

### Post by audiomick on 2010-07-11
> **mike555 said:**
> I think the one listed as vista is your restore partition ... by the way if you use it ,[COLOR=Red]it will mess up booting Ubuntu till you reinstall grub [/COLOR]..

Yeah, I know, thanks. If I were to need it, I would be more likely just to grow the Ubuntu partition... :)

Thanks for the answer.

---

### Post by Mark Phelps on 2010-07-11
> **audiomick said:**
> Hallo.
I have a dual boot with UNR and Win7 on a Lenovo ideapad. The Grub menu lists a Win7 loader and a Vista loader. I assume the Vista loader refers to the recovery partition of the original (win7) install.

Does anyone know if this is true, or if not, what the entry refers to?

Incidentally, Ubuntu runs really nicely on this machine.

thanks.

If the Lenovo came with Win7 preinstalled, they may have followed standard OEM practice of creating TWO partitions for Win7 -- one for the boot loader, the other for the OS and the remaining files.  The partition that does NOT contain the bootmgr folder (the larger partition) is the Win7 OS + files partition.  GRUB2 may report it as well because it contains winload.exe.

---

