---
title: "Computer Janitor:linux-headers-2.6.35-25 generic removal"
date: 2011-03-07
forum: General Help
---

### Post by gdiloren on 2011-03-07
To my surprse, I run computer janitor and it now tells me I no longer need this package (10 MB) linux-headers-2.6.35-25 generic  as it was updated last week to -27. Should I trust this and remove it safely???:)

---

### Post by Rubi1200 on 2011-03-07
In my opinion, you should not use Computer Janitor at all. It can, and will, remove things that may render your system unusable.

The safer way to remove older kernel versions and linux-headers is in Synaptic Package Manager.

It is always advisable to keep at least one older kernel for troubleshooting purposes.

See here for how to remove older kernels and clean up the GRUB menu:
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

### Post by ajgreeny on 2011-03-07
> **Rubi1200 said:**
> In my opinion, you should not use Computer Janitor at all. It can, and will, remove things that may render your system unusable.

The safer way to remove older kernel versions and linux-headers is in Synaptic Package Manager.

It is always advisable to keep at least one older kernel for troubleshooting purposes.

See here for how to remove older kernels and clean up the GRUB menu:
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)
+1
I totally agree with Rubi1200.

CJ can quite easily remove a lot of packages that you may have installed from ppa repos, or manually using "sudo dpkg -i" which is very annoying.

I don't think I have heard of it making a system un-bootable as Rubi suggests, but nevertheless, I don't trust such cleanup applications that seem to assume that you will have only installed packages from the standard repos.

---

