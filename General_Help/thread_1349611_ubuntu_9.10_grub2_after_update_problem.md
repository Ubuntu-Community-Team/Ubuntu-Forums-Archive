---
title: "ubuntu 9.10 grub2 after update problem"
date: 2009-12-08
forum: General Help
---

### Post by evazgecer on 2009-12-08
hi,

i am using windows 7 and in an other partition ubuntu 9.10. i installed ubuntu via wubi. i updated the grub2 but now in every start of ununtu a command line occurs like sh:grub>

i can boot ubuntu after the codes below:
```

>insmod ntfs
>set root=(hd0,5)
>loopback loop /ubuntu/disks/root.disk
>set root=(loop0)
>linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro
>initrd /boot/initrd.img-2.6.31-15-generic
>boot

```

But i have to do this every single restart. is there a permanent solution for me? i don't want to write any other. thanks...

---

