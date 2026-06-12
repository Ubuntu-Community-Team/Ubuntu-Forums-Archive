---
title: "Installing another distribution through kubuntu"
date: 2009-09-28
forum: General Help
---

### Post by Zeerak on 2009-09-28
Hey,

I have an ubuntu box, and I want to dual boot it with Gentoo, I just want to know if there is some way to install Gentoo while running ubuntu.
It's just it would make it a lot easier to install.
So if you could help that'd be great :-)

//Zeerak

---

### Post by Psycho.mario on 2009-09-28
You _might_ be able to do it with qemu. Create a partition with Gparted or something, lets say it's called /dev/sdb1, run:
```
qemu -cdrom ~/gentoo.iso -hda /dev/sdb1
```

IIRC, this should work, although some of the hardware detection might not work until you boot, also this way, you would need to manually edit /boot/grub/menu.lst

You probably would be better to install of a CD natively, because then it can detect your hardware and it might be able to add itself to your previous GRUB (Im not too sure about this in Gentoo)

---

### Post by Giblet5 on 2009-09-28
Sure. This box boots Suse, Gentoo, CentOS, Ubuntu32, Ubuntu x64, Redhat EL, Vista x64, XP32, and Win7 x64.

You just have to know how to do **manual** partitioning during the install and you have to *plan* your partition layouts. eg, all of my linux installs mount the same /home filesystem and share one large swap partition.

---

### Post by Psycho.mario on 2009-09-28
I think the OP meant he wanted to install the OS whilst booted into Ubuntu.
P.S. Impressive boot list :)

---

### Post by Zeerak on 2009-09-28
> **Psycho.mario said:**
> You _might_ be able to do it with qemu. Create a partition with Gparted or something, lets say it's called /dev/sdb1, run:
```
qemu -cdrom ~/gentoo.iso -hda /dev/sdb1
```

IIRC, this should work, although some of the hardware detection might not work until you boot, also this way, you would need to manually edit /boot/grub/menu.lst

You probably would be better to install of a CD natively, because then it can detect your hardware and it might be able to add itself to your previous GRUB (Im not too sure about this in Gentoo)

hmm I suppose you're right. It was pretty much just being able to use wifi on boot without configuring it until the install was done. Ah well. Booting from cd it is.
:-) thanks anyway.

And I did mean installing gentoo while booted into ubuntu.

And agreed. it is a very impressive bootlist :-)

---

### Post by Giblet5 on 2009-09-28
That would make a nice .sig:

"Any geek's intrinsic worth is directly proportional to the length of his Grub boot menu." :)

---

