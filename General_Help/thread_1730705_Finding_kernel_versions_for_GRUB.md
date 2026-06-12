---
title: "Finding kernel versions for GRUB"
date: 2011-04-16
forum: General Help
---

### Post by Kvothe on 2011-04-16
So, it turns out that I don't have my **Ubuntu** option in **GRUB** any more. I need the kernel version in order to add it to my list file. Any help? I can't boot it to find out because **GRUB** doesn't recognize it as an option. Any ideas?

---

### Post by PCaddicted on 2011-04-16
Type in "uname -r" without the quotes in the terminal. That will display the Kernel version.Use a LiveCD with the version of Ubuntu you have on your PC,otherwise you won't be able to boot and use the terminal.

---

### Post by oldos2er on 2011-04-16
> **Kvothe said:**
> So, it turns out that I don't have my **Ubuntu** option in **GRUB** any more. I need the kernel version in order to add it to my list file. 

What did you do to get it in that state? Are you using legacy grub or grub2? Which version of Ubuntu?

---

### Post by Kvothe on 2011-04-17
> **oldos2er said:**
> What did you do to get it in that state? Are you using legacy grub or grub2? Which version of Ubuntu?
I installed **Fedora**. **Legacy GRUB** right now as far as I know.

---

### Post by oldos2er on 2011-04-17
I believe you need to edit /boot/grub/menu.lst (or it may be grub.conf in Fedora, not sure) and manually add the kernels.

---

