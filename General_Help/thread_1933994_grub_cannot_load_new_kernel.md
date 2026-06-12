---
title: "grub cannot load new kernel"
date: 2012-03-01
forum: General Help
---

### Post by samanartorious on 2012-03-01
Let's open a discussion here:

I am tryin to install a Real Time kernel on my Ubuntu 11.04 Server machine with size 4GB. Before this, I am tryin to install a minimal kernel required in my Ubuntu 11.4 Desktop, but you know, the boot loader cannot load my new kernel. I have also tried the instruction on my Red Hat (CentOS 6) machine and ... again the same problem. boot loader stucks in loading my kernel, (i recall it was saying error with image number)

Here were the instructions:

1. tar xzf linux-2.6.31.6.tar
2. gunzip patch-2.6.31.6-rt19
3. cd linux-2.6.31.6 && patch p1 < ../patch-.6.31.6-rt19
4. make menuconfig (as I need a minimal kernel, I create .config using cat >> .config first)
5. make
6. make modules
7. make modules_install
8. make install (though this give the below output n finishes, but a window prompts n says that fglrx-8.840 cannot be installed or upgraded)

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.31.6-rt192.6.31.6-rt19
Found initrd image: /boot/initrd.img-2.6.31.6-rt192.6.31.6-rt19
Found linux image: /boot/vmlinuz-2.6.31.6-rt192.6.31.6-rt19.old
Found initrd image: /boot/initrd.img-2.6.31.6-rt192.6.31.6-rt19
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```9. I use update-initramfs and five the module folder in /lib/modules as the parameter:
```
sudo update-initramfs -c -k 2.6.31.6-rt19
```10. ```
update-grub
```You know, I have also tried compiling this kernel using other methods like:

```
cd linux-2.6.31.6 && patch p1 < ../patch-.6.31.6-rt19
make
make modules
make modules_install
cp arch/x86/boot/bzImage /boot/vmlinuz-version &&
cp Systems.map /boot/Systems.map-version
```then running initramfs and giving the /lib/modules/2.6.... as the parameter. Finally updating grub.

but again it cannot load my kernel. I also tried the dpkg debian mathod to install my new kernel using one of the ubuntu tutorials but again the same problem.
 Could anyone help me please to compile my new kernel.

> 
I would also thank if you mention how I can transfer my compiled kernel in my laptop to the 4GB machine. I think if I copy the compiled bzImage on my laptop there. But don't know about the compiled modules and... I'd thank if you mention everything precisely.
> 
when I choose recovery mode in boot loader it gives me the following notification n it stucks
loading linux 2.6.31.6-rt19 ...
loading initial ramdisk ...
I also added the nomodeset at the end of linux line in boot menu but nothing changed!
Regards

---

