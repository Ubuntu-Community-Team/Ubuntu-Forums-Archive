---
title: "wubi install, windows reinstall, get back ubuntu on boot menu?"
date: 2009-11-24
forum: General Help
---

### Post by soumen08 on 2009-11-24
Hello,
One of my friends had installed ubuntu on his D: drive via the wubi install. Now owing to a windows reinstall, his MBR has been overwritten, and since ubuntu isnt installed to a separate partition, i cant install grub from the live cds like i used to in these cases. How do i get a bootable ubuntu entry into the windows bootloader?
regards
Soumen

---

### Post by Mark Phelps on 2009-11-25
If you're asking to install GRUB to get back into Ubuntu on the wubi-installed machine -- you can't.  

When MS Windows was reinstalled, it wiped out the Wubi install.  There is no Ubuntu instance there anymore.

---

### Post by soumen08 on 2009-11-25
I pretty much knew it was hopeless.. thanks anyway :)
regards
Soumen

---

### Post by monkeyoutlaw on 2009-11-25
Surely there is a way if the disk has not been formatted? The data is still there in the 'fake partition / file', just the MBR needs recreating....?

---

### Post by soumen08 on 2009-11-25
running grub isnt the problem, way i see it, to setup grub on a system, it has to see its files which it will master onto the MBR.
regards
Soumen

---

