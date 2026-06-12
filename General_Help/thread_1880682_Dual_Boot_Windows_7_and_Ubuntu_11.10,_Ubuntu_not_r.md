---
title: "Dual Boot Windows 7 and Ubuntu 11.10, Ubuntu not recognized"
date: 2011-11-14
forum: General Help
---

### Post by johntkucz on 2011-11-14
Hey, I partitioned hard drive, installed Ubuntu 11.10 with swap and isntalled a bunch of apps on it.  Then in gparted I partitioned a partition NTFS for windows.  I booted off windows 7 home premium cd and installed windows onto the NTFS partition I made. 

Now when I boot up I don't have an option to boot in ubuntu??

The computer is a dell n4010. Thanks.

I already tried installing with wubi (on same partition as ntfs) and disliked that.  I must install ubuntu and windows on sep. partitiosn because it's cleaner and doesn't lead to permission problems at times (like sometimes couldn't change partitions on a diff. partition that was deemed scratch). and I have done that it's just that now ubuntu isn't recognized in startup.

both the win and ubuntu partitions were obviously primary and the ubuntu was ext4. thanks

---

### Post by johntkucz on 2011-11-14
tldr;

I successfully installed ubuntu on an ext4 partition.

THEN

I successfully installed windows on an ntfs partition.


Now, when I boot, despite the ubuntu partition existing, it is not recognize and I don't have the option of booting into ubuntu (just windows).


would appreciate an informative response asap.

---

### Post by johntkucz on 2011-11-14
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

bollocks.  appears may have to reinstall ubuntu *after* windows bollocks dang.


I can do that but there has to be away of reaccessing that. wondering how.

What's the windows bootloader?  It automatically erases grub or something?

---

### Post by Hylas de Niall on 2011-11-14
You should just be able to reinstall Grub, rather than the whole shebang. Windows as you now know, doesn't like sharing the bed with other OS's.
Trawl this very forum for the term 'grub' and you'll get some great pointers how to do that.

---

### Post by dandnsmith on 2011-11-14
> **johntkucz said:**
> [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
appears may have to reinstall ubuntu *after* windows bollocks.
I can do that but there has to be away of reaccessing that. wondering how.
What's the windows bootloader?  It automatically erases grub or something?

Windows (any flavour) is renowned for overwriting the primitive bootloader in the MBR without so much as a by-your-leave, so what you need is **grub-install** with the correct parameters. There was a recent post spelling out the detail on how to do this from a LiveCD - hopefully the one you used for the Ubuntu install.
After the grub-install, you'll find (possibly) that you windows isn't in the grub menu list - is it isn't you will want an **update-grub** to rebuild the list.

HTH

---

