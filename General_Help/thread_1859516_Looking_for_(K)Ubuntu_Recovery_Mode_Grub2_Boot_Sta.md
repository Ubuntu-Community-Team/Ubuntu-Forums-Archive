---
title: "Looking for (K)Ubuntu Recovery Mode Grub2 Boot Stanza"
date: 2011-10-13
forum: General Help
---

### Post by iClouseau88 on 2011-10-13
Hi everyone,

I have a multiboot system in which openSUSE 11.4 has the default legacy GRUB boot loader which boots all other OS's such as Windows, Fedoras and Buntus.

The following is part of my openSUSE's /etc/boot/grub/menu.lst:

The first part boots into Kubuntu easily:

```

###Add Kubuntu 11.10 KDE 64
title Kubuntu 11.10  KDE_64 (via chainloading)
    rootnoverify (hd0)
    kernel (hd0,9)/boot/grub/core.img

```

However, the following part DOES NOT:

```

###Kubuntu 11.10 KDE 64 (Recovery Mode)
title Kubuntu 11.10 Beta2 KDE_64 (recovery mode)
    set root =(hd0,9)
    kernel (hd0,9) /boot/vmlinuz-3.0.0-12-generic root=/dev/sdb10 ro recovery nomodeset
    initrd (hd0,9) /boot/initrd.img

```

I am looking for help from Grub2 experts like drs305, so that if/when updating, (K)Ubuntu fails to boot due to some bugs I can resort to Recovery Mode, just like when one has (K)Ubuntu in a single PC or in a dual-boot Windows-Ubuntu system.

Any suggestions?  Thanks in advance

---

### Post by iClouseau88 on 2011-10-14
Dear Moderator,

Could you please move my thread as a new post to Grub2 Basics by drs305 in the Tutorials sub-forum, where replies would be informative and relevant?  I recognized I made a mistake, since I should have posted there in the beginning.

Thank you kindly for your help.

---

