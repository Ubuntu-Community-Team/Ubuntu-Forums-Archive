---
title: "Custom kernel compile"
date: 2010-07-31
forum: General Help
---

### Post by inp3dance on 2010-07-31
Hi,
I'm using Ubuntu 10.04.
Following this tutorial [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")I tried to compile a custom kernel for my ubuntu.
The source I used was 2.6.35-rc6, downloaded from kernel.org with no patches applied on it.
I made the kernel packages with 
```
fakeroot make-kpkg --initrd kernel_image kernel_headerses 
```

The packages just installed fine, but there is no initrd image for the custom kernel in boot directory, so I can't boot the new kernel.

Can somebody help me with this pls, how can I generate an initrd image?

I compiled custom kernels many times on openSUSE, so I am familiar with the kernel compilation procedure, but not with the Ubuntu way.

I also read the documentation for 10.04 from [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile"), but that stuff seems to me way overcomplicated compared to openSUSE.

Thank you!

---

### Post by WorMzy on 2010-07-31
From the second link you posted:

> Since Ubuntu Lucid (10.04) the image postinst no longer runs the initramfs creation commands. Instead, there are example scripts provided that will perform the task. These scripts will work for official kernel images as well. For example 
```
sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postinst.d/initramfs /etc/kernel/postinst.d/initramfs
sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postrm.d/initramfs /etc/kernel/postrm.d/initramfs
```

Note: I couldn't get the above scripts to help in generating an initrd for the kernel - and so the built kernel couldn't boot; the only thing that worked for me was the recommendation in [http://www.debian-administration.org/article/How_Do_I_Make_an_initrd_image](http://www.debian-administration.org/article/How_Do_I_Make_an_initrd_image), "use initramfs command. It is real solution."; what I used (after the custom built kernel's *.deb's were installed), was:

```
cd /boot
sudo mkinitramfs -k -o initrd.img-2.6.32.15+drm33.5-mylucid 2.6.32.15+drm33.5-mylucid
sudo update-grub2
```

---

### Post by inp3dance on 2010-07-31
Thank you WorMzy!

---

