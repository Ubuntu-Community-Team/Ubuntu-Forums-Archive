---
title: "Computer reboots before GRUB loads"
date: 2011-02-20
forum: General Help
---

### Post by Wolfos on 2011-02-20
Hi, I've installed Ubuntu inside Windows 7 with the Ubuntu Windows installer.

I have previously had problems with booting Ubuntu, but it always got to GRUB at least. Now it shows the Windows bootloader, I select Ubuntu and the computer just reboots.

---

### Post by Miguel Tavares on 2011-02-20
does it drop you to a shell?

---

### Post by Acheron3 on 2011-02-20
Can you post *grub.cfg* contents? It's normally located under /boot/grub.

---

### Post by kiyop on 2011-02-20
Wubi?
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

If you installed with Wubi, the filesystem may be (in) /ubuntu/disks/root.disk.
And maybe, the boot loader and its configuration files reside in /wubildr and are not correctly set-up.

My iso file with script incorporated in initramfs with kexec will help you. But I think I should not make you download my iso file.

If you can use RIP linux
[http://rip.7bf.de/current/](http://rip.7bf.de/current/)
you may be able to boot the system,
```

# mkdir /testmount1 /testmount2
# mount -t ntfs-3g /dev/[COLOR=red][device file name of the partition containing /ubuntu/disks/root.disk][/COLOR] /testmount1
# mount -o loop /testmount1/ubuntu/disks/root.disk /testmount2
# kexec -l /testmount2/vmlinuz --initrd=/testmount2/initrd.img --append="root=/dev/[COLOR=red][device file name of the partition containing /ubuntu/disks/root.disk][/COLOR] loop=/ubuntu/disks/root.disk ro"
# kexec -e
```, if you did not separate /boot partition from root(/) partition.

---

### Post by Rubi1200 on 2011-02-20
> **Wolfos said:**
> Hi, I've installed Ubuntu inside Windows 7 with the Ubuntu Windows installer.

I have previously had problems with booting Ubuntu, but it always got to GRUB at least. Now it shows the Windows bootloader, I select Ubuntu and the computer just reboots.
Hi and welcome to the forums :-)

The best advice I can give you right now is to read the [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198").

The answers to your problem are there, but if you need help with anything feel free to ask.

---

