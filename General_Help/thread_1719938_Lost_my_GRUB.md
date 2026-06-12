---
title: "Lost my GRUB"
date: 2011-04-02
forum: General Help
---

### Post by dirtynorth on 2011-04-02
I installed Windows 7 on a seperate partition a few weeks ago s I could use some specialized software.  After the install it seems like my Ubuntu partiton is still there but I cant seem to boot into it.  When i turn the computer on i dont see the GRUB screen anymore.  Did windows somhow eat my GRUB??  If so how do I get it back??

Thanks

---

### Post by wilee-nilee on 2011-04-02
Assuming Ubuntu is still there and running grub2 you need to load the grub bootloader into the MBR of the HD it is in, and make sure it is first read in the bios.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

