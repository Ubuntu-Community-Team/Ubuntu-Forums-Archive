---
title: "Dual boot with Arch LINUX"
date: 2011-03-04
forum: General Help
---

### Post by Xi0N on 2011-03-04
Im installing ubuntu in the same HD as I have Arch LINUX on... 
Ubuntu's root is in /dev/sda7 (ext4) and im trying to add an entry in arch's grub so that i can switch to Ubuntu's GRUB menu..... but i seem to not be able to figure out how.....
When asked where to install the bottloader, i chose /dev/sda7 (i dont want to wreck arch linux's current boot loader)
Can anyone shed some light on this issue?
Thanks!!!

---

### Post by WorMzy on 2011-03-04
You don't need to install a boot loader if you're going to continue using Arch's grub legacy. Just boot into Arch (or mount Arch's partition from Ubuntu), open up /boot/grub/menu.lst with your favourite text editor in root mode (e.g. "gksu gedit /boot/grub/menu.lst" from Arch, or "gksu gedit /media/archpartition/boot/grub/menu.lst" from Ubuntu)

Then copy-paste Arch's entry, and modify it so that it points to Ubuntu's partition + kernel.

You'll need to add

```
root (hd0,6)
```

(I think) to the start of Ubuntu's entry for it to know where you're looking.

---

### Post by wilee-nilee on 2011-03-04
Just for clarification grub2 will read grub legacy automatically. If you had put the grub2 bootloader in the mbr you would have a grub2 menu at boot with a choice of all the OS's. 

Use which ever suits you though.

---

