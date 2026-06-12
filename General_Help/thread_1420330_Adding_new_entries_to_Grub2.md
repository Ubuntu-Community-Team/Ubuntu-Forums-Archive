---
title: "Adding new entries to Grub2"
date: 2010-03-02
forum: General Help
---

### Post by CRMR on 2010-03-02
hi...,

i'm using ubuntu 9.10... i'm working on some projects on L4 microkernel... i want to add it to the grub...
i was familiar with the earlier grub, i.e editing the menu.lst...

title = L4Ka::Pistachio/i586 pingpong
kernel=/boot/kickstart
module=/boot/i586-kernel
module=/boot/sigma0
module=/boot/pingpong

how can i do this in new grub version...??? 

i tried adding the following to /etc/grub.d/40_custom but failed... 
menuentry "L4Ka::Pistachio" {
set root=(hd0,9)
kernel=/boot/kickstart
module=/boot/sigma0
module=/boot/pingpong
}

---

### Post by Alaric on 2010-03-02
This link should point you in the right direction.  

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by darolu on 2010-03-02
I think the line "kernel=/boot/kickstart" should be:
```
linux /boot/kickstart
```

I'm not very familiar with Grub2 (yet) so you may want to read this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2010-03-03
What boot loader does that system use. If you can install the bootloader to the sda9 partition then you can chainboot. Grub2 does not like to be installed to a partition but grub legacy works just fine in a partition.

# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd0,9)
    chainloader +1
}

---

