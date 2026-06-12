---
title: "Initramfs - fail to mount /dev, /sys and /proc in /root"
date: 2010-09-03
forum: General Help
---

### Post by Kdar on 2010-09-03
[[IMG]http://img405.imageshack.us/img405/8382/dscf6440.th.jpg[/IMG]](http://img405.imageshack.us/i/dscf6440.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Here was I get on my screen.

I don't know why this is happened. But before I rebooted, I could not see any content on Windows like update or shut-down (if I tried to install something and it asked for confirmation, that window was blank. Or before I shut down, I had to push enter, since that windows was blank.)

I don't think I installed anything and computer was working just fine before.

Can someone tell me what I can do? I don't want to reinstall everything again.

---

### Post by surfer on 2010-09-03
if you have an old kernel and initramfs, try to boot with that.

otherwise you will have to boot with a cd (or usb stick) into the ubuntu rescue mode, mount your root filesystem, mount /sys /proc /dev (with the --bind option), chroot into the root filesystem and run update-initramfs.

---

### Post by Kdar on 2010-09-03
> **surfer said:**
> if you have an old kernel and initramfs, try to boot with that.

otherwise you will have to boot with a cd (or usb stick) into the ubuntu rescue mode, mount your root filesystem, mount /sys /proc /dev (with the --bind option), chroot into the root filesystem and run update-initramfs.

How do I do first option?

I don't think it I can access grub?

---

### Post by surfer on 2010-09-03
oh, your grub is gone too? then the first option will not work... your error message comes from the initrd, which is loaded right after the kernel. so you seem to have some bootloader. or is your grub just not displaying a menu?

---

### Post by Kdar on 2010-09-03
> **surfer said:**
> oh, your grub is gone too? then the first option will not work... your error message comes from the initrd, which is loaded right after the kernel. so you seem to have some bootloader. or is your grub just not displaying a menu?

well, maybe just not displaying. If it not displaying can I stop it before it executes?

---

### Post by ajgreeny on 2010-09-03
Hit shift and hold it down when you turn on and grub menu should appear.

---

