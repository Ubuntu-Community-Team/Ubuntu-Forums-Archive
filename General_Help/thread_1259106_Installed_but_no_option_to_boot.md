---
title: "Installed but no option to boot"
date: 2009-09-05
forum: General Help
---

### Post by bbx1000 on 2009-09-05
Hi there

I am new to ubuntu, just installed it on PC, I got windowsXP there first, then I have installed the ubuntu 9.04 successfully, but when i reboot the pc, it does not give me any option to boot into ubuntu, it just boot directly into windows. 

I have tried to install a few times, using different options, like "install side by side", "use the large continue space", "on second hard drive" but no luck, still end up the same.

any idea.

p.s. i can boot from the liveCD and it works fine.

---

### Post by c0mput3r_n3rD on 2009-09-06
Make sure you're partitioning the hard drive correctly.  Find a set of instructions for install Ubuntu to dual boot.  If you install correctly, the linux boot loader will ad an option page to pick your OS.
[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

---

### Post by jobst on 2009-09-06
> **bbx1000 said:**
> Hi there

I am new to ubuntu, just installed it on PC, I got windowsXP there first, then I have installed the ubuntu 9.04 successfully, but when i reboot the pc, it does not give me any option to boot into ubuntu, it just boot directly into windows. 

I have tried to install a few times, using different options, like "install side by side", "use the large continue space", "on second hard drive" but no luck, still end up the same.

any idea.

p.s. i can boot from the liveCD and it works fine.


Its because windows boot loader doesnt know anything about ubuntu, follow the instruction about how to get the GRUB boot sector, save it and put that into your windows install:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)


jobst

---

