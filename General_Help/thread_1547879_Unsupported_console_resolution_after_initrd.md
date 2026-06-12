---
title: "Unsupported console resolution after initrd"
date: 2010-08-07
forum: General Help
---

### Post by krispzz on 2010-08-07
Hi everybody. I debootstrapped an install into an existing lvm and booted into it and everything is working great except that after initrd hands off to boot the real root, the text font changes and the resolution is unsupported by my old monitor. The box is up and running because I can ssh in. This is more of an annoyance than anything as I only use the console when something is broken, but it does need to be resolved.

I used dpkg-reconfigure console-setup as described in the debootstrap config guide but I don't see an option for changing the "vga" statement before it regenerates the initrd.

Any suggestions?

Kind regards!
Dave

---

### Post by dino99 on 2010-08-07
i always remove this weird "vga=xxx" due to issue it generate, then run update-grub again (/etc/default/grub)

---

### Post by krispzz on 2010-08-07
Hello and thanks for the quick response. I'm still using legacy grub until I fully migrate over to ubuntu, and I am not passing a vga=xxx option to the kernel. I can see it boot the kernel and initrd, but once it hands it off to the init it changes the font and resolution. I'm looking for where I can change this behavior.

thanks again!
Dave

---

