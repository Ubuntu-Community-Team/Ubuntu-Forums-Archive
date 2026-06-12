---
title: "How do I boot Ubuntu manually from GRUB?"
date: 2009-11-14
forum: General Help
---

### Post by Ceaserian Øgly on 2009-11-14
I am having a problem with booting Ubuntu. When I try to do so, I am met with a GRUB commandline. I have the feeling that I have to boot the kernel manually from there, by typing "linux [kernel name]". If this is the case, would anyone know what I should type as the name of the kernel?

I use a dual boot with Ubuntu 9.10, installed by Wubi. I *did* force quit before this problem occured, because I had problems with rebooting. I also had this problem when I first installed Ubuntu 9.10 (I reinstalled it instead of upgrading from 9.04), but I solved it by reinstalling it again, because it was an option back then.

---

### Post by Mark Phelps on 2009-11-14
You said you installed 9.10 using Wubi -- so which MS Windows OS did you install it inside? XP, Vista, or Seven?

---

### Post by undecim on 2009-11-14
Try this.```
    insmod ext2
    set root=(hd0,1)
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
```

This is assuming that Ubuntu is installed on the first partition of the first drive in the machine. If it isn't, you will need to edit the (hd0,1) and root=/dev/sda1 parts accordingly. Also, if you have a previous kernel version, you will need to type your version.

---

### Post by Ceaserian Øgly on 2009-11-16
> **Mark Phelps said:**
> You said you installed 9.10 using Wubi -- so which MS Windows OS did you install it inside? XP, Vista, or Seven?
I suppose that would be relevant information. It was XP Professional.

> **undecim said:**
> Try this.```
    insmod ext2
    set root=(hd0,1)
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
```This is assuming that Ubuntu is installed on the first partition of the first drive in the machine. If it isn't, you will need to edit the (hd0,1) and root=/dev/sda1 parts accordingly. Also, if you have a previous kernel version, you will need to type your version.
Thank you, but it didn't work. I probably typed in the wrong kernel version. I don't know exactly what version I have. Is there any way to find out through GRUB or a live-CD? I downloaded it on 31 October, if that can be used to find it out.

I notice that I accidentally labelled this with "kubuntu" instead of "ubuntu. Why do I always appear so silly when I join a new forum? :(

---

### Post by JoelOl75 on 2009-11-16
Tab completion may help you not misspell.

---

### Post by JBAlaska on 2009-11-16
And if your on a laptop with a recovery partition you may have to modify the lines as so:
```
insmod ntfs
set root=(hd0,[COLOR="Red"]2[/COLOR])
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
**linux /boot/vmlinuz-2.6.31-14-generic root+/dev/sda[COLOR="Red"]2[/COLOR] loop=/ubuntu/disks\ /root.disk ro quiet splash**
initrd /boot/initrd.img-2.6.31-14-generic
```

---

### Post by Ceaserian Øgly on 2009-11-24
When I try to boot my kernel with the linux command, the file is not found. Tab completion doesn't work.

I don't know what kernel version I have, and I don't know whether I have a recovery partition or not. I do however know that I have a laptop. How do I find out about my kernel and partition?

---

