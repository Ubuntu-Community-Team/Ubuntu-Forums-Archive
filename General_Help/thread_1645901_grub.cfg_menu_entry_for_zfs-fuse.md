---
title: "grub.cfg menu entry for zfs-fuse"
date: 2010-12-15
forum: General Help
---

### Post by Beeblebox on 2010-12-15
I am trying to set up a disk with root on zfs.  The disk has a separate partition for grub and users grub2 as the loader.  I have already specified the [COLOR=Green]insmod zfs[/COLOR] setting and the grub command line shows zfs commands as loaded - so no problem there.

When the boot process for the root located on zfs starts, it hangs fairly early and I think it's because of my wrong menu entry.  I read someplace that zfs labels would be listed under[COLOR=Green] /dev/zpool/something[/COLOR], but [COLOR=Green]dev[/COLOR] has no [COLOR=Green]zpool[/COLOR] nor [COLOR=Green]zfs[/COLOR] sub-directory.

```
grub-probe
update-grub
```etc are no help, looks like this has to be done by hand. [COLOR=Green]grub.cfg[/COLOR] entry for this boot is below.  ROOT=ID= number is from zfs output matching ID=number.

```
menuentry 'Ubuntu on zfs' --class ubuntu --class gnu-linux --class gnu --class os {
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 62db7b41-412f-46b8-b207-2a831e082b50
    linux    /vmlinuz-2.6.32-21-generic root=ID=8085587268725868351 ro   verbose
    initrd    /initrd.img-2.6.32-21-generic
}
```

---

