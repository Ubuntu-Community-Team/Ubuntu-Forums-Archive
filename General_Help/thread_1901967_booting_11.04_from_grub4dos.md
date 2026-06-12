---
title: "booting 11.04 from grub4dos"
date: 2011-12-29
forum: General Help
---

### Post by carbquick on 2011-12-29
I have a dualboot situation with XP and ubu 11.04; originally, I simply used the grub2 bootup menu.
Then for various reasons, I installed grub4dos to the mbr. I can't figure out what the menu.lst entry
should be to boot up 11.04 from the grub4dos menu. I can still boot up the ubu using the grub2 on a 
ubcd rescue image, but this is tedious. In the earlier ubu's,using the old grub, it was straightforward
to copy the menu.lst from the grub in linux, but grub2 doesn't use menu.lst, uses grub.cfg.
   Anybody know how to do this?  Tnx,carbquick.:confused:

---

### Post by grahammechanical on 2011-12-29
Have you seen this?

[http://diddy.boot-land.net/grub4dos/files/embedded.htm]("http://diddy.boot-land.net/grub4dos/files/embedded.htm")

Grub4dos looks for a menu.lst file. So, you need to create one in the same style of the legacy Grub menu.lst file.

Regards.

---

### Post by carbquick on 2011-12-29
> **grahammechanical said:**
> Have you seen this?

[http://diddy.boot-land.net/grub4dos/files/embedded.htm](http://diddy.boot-land.net/grub4dos/files/embedded.htm)

Grub4dos looks for a menu.lst file. So, you need to create one in the same style of the legacy Grub menu.lst file.

Regards.
grahammechanical,
      Tnx for the reply. I already have a menu.lst file for the grub4dos, with several entries, all of which work;
the problem is that the older format(grub) doesn't seem to work with the 11.04 distro. In fact, the ubu 11.04
hase a file in /boot/grub called 'core.img', which if you try to go there with grub4dos, says there is an
unsupported executable format (supposedly in core.img). 
      The old way of (menu.lst)ing to vmlinuz/initrd doesn't see to work with 11.04. carbquick. :-k

---

### Post by jjex22 on 2011-12-29
> **carbquick said:**
> grahammechanical,
      Tnx for the reply. I already have a menu.lst file for the grub4dos, with several entries, all of which work;
the problem is that the older format(grub) doesn't seem to work with the 11.04 distro. In fact, the ubu 11.04
hase a file in /boot/grub called 'core.img', which if you try to go there with grub4dos, says there is an
unsupported executable format (supposedly in core.img). 
      The old way of (menu.lst)ing to vmlinuz/initrd doesn't see to work with 11.04. carbquick. :-k

hmm...

```

root (hd0,x)
kernel /boot/grub/core.img

```

should work i'd have thought, just remember that x is your root partition minus 1. though if grub2 originally installed to your mbr and has been overwritten, it may need to be reinstalled - from ubuntu 
```

sudo grub-install /dev/sdax
sudo update-grub

```

set x to either your root partition or boot partition ... or if you want to get rid of grub4dos and just use grub2 just get rid of the x!

---

### Post by carbquick on 2011-12-30
jjex22,
     Amazing; I must be getting senile! I didn't think that grub4dos would/could work by booting grub2 in the linux partition!
Didn't even have to reinstall the grub2 on it's partition. Tnx, carbquick.

---

### Post by jjex22 on 2011-12-30
> **carbquick said:**
> jjex22,
     Amazing; I must be getting senile! I didn't think that grub4dos would/could work by booting grub2 in the linux partition!
Didn't even have to reinstall the grub2 on it's partition. Tnx, carbquick.

Glad it helped :)

It is chainloading, but the only way I've found to get ubuntu 11.x to boot from menu.lst entries without using grub2 to point it directly at the kernel, and then you have to change the entry every time ubuntu update the kernel... which is annoying!

---

