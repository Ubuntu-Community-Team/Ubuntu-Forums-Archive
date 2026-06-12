---
title: "duel boot"
date: 2010-05-12
forum: General Help
---

### Post by FM101 on 2010-05-12
Hello,
I have some questions on duel boot setup.
If you create a duel boot setup, how can you remove the ubuntu partition, if you no longer need it?
I wouldn't think just removing the partition would do it.
Wouldn't the boot manager still come up?
How can you remove it all?

thanks

---

### Post by Nxion on 2010-05-12
> **FM101 said:**
> Hello,
I have some questions on duel boot setup.
If you create a duel boot setup, how can you remove the ubuntu partition, if you no longer need it?
I wouldn't think just removing the partition would do it.
Wouldn't the boot manager still come up?
How can you remove it all?

thanks


Honestly if this is the first time you have used ubuntu or am installing Ubuntu for the first time, I would [try Wubi.]("http://wubi-installer.org/") With Wubi, you don't have to worry about partitions, it just make an entry in the Add/remove programs in the Windows control panel, so if you don't want ubuntu anymore, you can remove it and not worry about.

---

### Post by adam22 on 2010-05-12
If you want to set up a dual boot, the first thing you need to do is defrag your hard drive twice, for good measure.

You then need to shrink Windows. If you install Ubuntu and get rid of it, you can expand Windows to fill the entire disc again. Deleting Ubuntu should default back to the Windows bootloader, instead of Grub2.

---

### Post by Nxion on 2010-05-12
> **adam22 said:**
> If you want to set up a dual boot, the first thing you need to do is defrag your hard drive twice, for good measure.

You then need to shrink Windows. If you install Ubuntu and get rid of it, you can expand Windows to fill the entire disc again. Deleting Ubuntu should default back to the Windows bootloader, instead of Grub2.

I have tried this and it actually does not bring back the original windows boot loader. It has to be restored with a windows 7 or vista disk. There is an option to restore boot loaded when you boot off the system disk.

---

### Post by adam22 on 2010-05-12
> **Nxion said:**
> I have tried this and it actually does not bring back the original windows boot loader. It has to be restored with a windows 7 or vista disk. There is an option to restore boot loaded when you boot off the system disk.

I'm almost certain that I deleted my linux partition at some point and booted right into Windows without a problem, but I may be wrong.

---

