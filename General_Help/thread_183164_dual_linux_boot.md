---
title: "dual linux boot"
date: 2006-05-27
forum: General Help
---

### Post by paracetamolo on 2006-05-27
I installed ubuntu and then suse, I haven't seen any option to use the old grub I had so I told suse to install grub again.
now the problem is that when I upgrade the ubuntu kernel grub(suse) can't see it and  boot the old one.](*,) 

how can I tell grub(suse) to boot the new kernel?

I think that if I had installed suse with the ubuntu grub I would have experienced the same issue with suse, am I wrong? how does people with multi-distro-boot manage this?:-k 
thanks:D

---

### Post by Ubuntuud on 2006-05-27
Try reinstalling grub...

---

### Post by Sutekh on 2006-05-29
[quote=paracetamolo]I installed ubuntu and then suse, I haven't seen any option to use the old grub I had so I told suse to install grub again.
now the problem is that when I upgrade the ubuntu kernel grub(suse) can't see it and  boot the old one.](*,) 

how can I tell grub(suse) to boot the new kernel?

I think that if I had installed suse with the ubuntu grub I would have experienced the same issue with suse, am I wrong? how does people with multi-distro-boot manage this?:-k 
thanks:D[/quote] Yep it can be tricky and definately a pain.

I usually install GRUB from later Linux installations on the install partition, keeping the original GRUB on the MBR.  This works best for because, when any GRUB is updated with a kernel upgrade I just copy the new entry from that GRUB to the MBR GRUB.

Confusing? ;)

The other way (very similar) is to manually edit the GRUB that does the actual booting.  A fairly typical GRUB entry looks like
```
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
** kernel          /boot/vmlinuz-2.6.12-9-386** root=/dev/hda1 ro quiet splash
** initrd          /boot/initrd.img-2.6.12-9-386**
savedefault
boot

``` All you need to do is edit the kernel line and initrd line to reflect the newer kernel.  So if my kernel was updated to say 2.6.12-10-386, I'd change GRUB to
```
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
** kernel          /boot/vmlinuz-2.6.12-10-386** root=/dev/hda1 ro quiet splash
** initrd          /boot/initrd.img-2.6.12-10-386**
savedefault
boot

``` 
OR you can use the automatic symlinks in the root folder (/) that point to the most recent and next most recent kernel image and initial ramdisc.
```
title           Ubuntu, latest kernel
root            (hd0,0)
**kernel          /vmlinuz** root=/dev/hda1 ro quiet splash
**initrd          /initrd.img**
savedefault
boot

```   You can check out these links to see where they go.```
ls -l /vmlinuz*
ls -l /initrd.img*
```

---

