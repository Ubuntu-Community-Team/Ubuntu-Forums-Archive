---
title: "Gnu grub?"
date: 2009-12-09
forum: General Help
---

### Post by Rockanium on 2009-12-09
```
GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible
 command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>_
```


Ubuntu will not boot D:



this has happend to me once before, and i had to reinstall ubuntu. this time i have very important documents and i do not want to start again.

Before this happend the computer was frozen so i restarted it, then this happend.

---

### Post by bsh on 2009-12-10
you can try and boot a kernel using the grub shell, then fix whatever caused it to stop at the shell and not boot.
[grub2 shell commands]("http://grub.enbug.org/Manual#GrubShell")
or you could use a live cd to boot and then backup your valuable files off the hard disk to another location, before you try to fix anything.
i personally don't like grub2 (yet), but you can go back to the "legacy" grub, if you are more familiar with it.

---

