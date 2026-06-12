---
title: "Grub2 with Multiple Linux Installs"
date: 2009-12-07
forum: General Help
---

### Post by jlward4th on 2009-12-07
I have Karmic on sda1 and Lucid on sda2 (and Windows 7 on sdb).  But I can't get grub2 to see both Karmic and Lucid.  Here is the output from update-grub on Karmic:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Adding Windows 7
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows 7 (loader) on /dev/sdb2
done
```

Here is the update-grub on Lucid:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-7-generic
Found initrd image: /boot/initrd.img-2.6.32-7-generic
Adding Windows 7
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
```

How can I get a grub2 config that can boot either Karmic or Lucid?  Thanks!

---

### Post by jlward4th on 2009-12-07
Figured this one out.  When I duplicated my filesystem for Lucid I didn't give the new partition a new uuid.  To do that I did:
```
tune2fs -u random /dev/sda2
```

That fixed the problem.

---

### Post by Ziggy72 on 2010-01-31
Thank you. I've been looking for a solution to that problem. Use, e.g.:
```

tune2fs -U random /dev/sda2
update-grub

```

---

