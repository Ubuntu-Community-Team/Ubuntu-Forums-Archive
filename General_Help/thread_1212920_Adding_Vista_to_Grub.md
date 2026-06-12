---
title: "Adding Vista to Grub"
date: 2009-07-14
forum: General Help
---

### Post by Georgie.Mathews on 2009-07-14
Hi all  i installed Vista after Ubuntu and lost Grub. Then using the Super Grub disk I restored my Grub, however Vista is not lsited in the Grub entries. 

I found this :
> This is assuming Windows is the first partition on first disk
Add this entry to your /boot/grub/grub.conf


title Windows
root (hd0,0)
savedefault
makeactive
chainloader +1

However, how do i know what drive number and partition number my Vista is on? For example is sda1 equivalent to (hd0,0) in Grub?

---

### Post by coffeecat on 2009-07-14
> **Georgie.Mathews said:**
> For example is sda1 equivalent to (hd0,0) in Grub?

Yes, grub counts from zero. sda1 = (hd0,0) ; sdb3 = (hd1,2) ; and so on.

Are you sure your Vista partition is on sda1? Some OEM maufacturers put a restore utility on the first partition. If you need any help, post the terminal output of:

```
sudo fdisk -l
```

**Edit:** by the way....

> Add this entry to your /boot/grub/grub.conf

In Ubuntu, the grub configuration menu is /boot/grub/menu.lst. Some distros use menu.lst; others grub.conf; some have both, one of which is a link to the other; but Ubuntu has just menu.lst.

---

### Post by Georgie.Mathews on 2009-07-15
Thanks, great success!

---

