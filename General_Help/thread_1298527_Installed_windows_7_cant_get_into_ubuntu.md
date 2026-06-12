---
title: "Installed windows 7 cant get into ubuntu"
date: 2009-10-22
forum: General Help
---

### Post by xxterry1xx on 2009-10-22
Hey i just installed windows 7 and ubuntu is gone so is grub but i want to have ubuntu in windows loader
 
 
 
i have 2 harddrives
first one is with windows 7 (NFTS)
second is with ubuntu 9.04 (EXT3)

---

### Post by cariboo on 2009-10-23
Use this [howto]("http:///ubuntuforums.org/showthread.php?t=224351") to reinstall grub.

---

### Post by fluffman86 on 2009-10-23
And yes, you *have* to use GRUB instead of the Windows boot loader, because windows cannot read the linux file system to boot from it.

---

### Post by oldfred on 2009-10-23
You cannot. Windows does not boot ubuntu unless it is a wubi install.

You can switch drives in BIOS and put GRUB in the ubuntu drive. You then can add a windows boot stanza to menu.lst to choose either ubuntu or windows.

If you want in the future you can in BIOS switch drives and boot directly into windows but it will not see the ubuntu drive.

---

### Post by xxterry1xx on 2009-10-23
> **cariboo907 said:**
> Use this [howto]("http:///ubuntuforums.org/showthread.php?t=224351") to reinstall grub. the link is dead

---

