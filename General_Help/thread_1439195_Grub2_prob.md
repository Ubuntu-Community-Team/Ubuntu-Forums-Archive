---
title: "Grub2 prob"
date: 2010-03-25
forum: General Help
---

### Post by lvalen18 on 2010-03-25
On Grub legacy i used a menu entry to boot from a DVD since the bios on my pc doesn't recognize my DVD burner.... So before on the old grub i can just added this menu entry and it all worked...

title 		DVD

root		(hd0,0)

kernel 		/boot/grub/memdisk.bin

initrd 		/boot/grub/sbootmgr.dsk

then grub 2 came along and that all changed..
on the 40_custom file i added this

menuentry "Boot DVD Drive" {
        set root=(hd0,0)
        linux   /boot/grub/memdisk.bin
        initrd  /boot/grub/sbootmgr.dsk
}

i don't know if thats right or not but it does show up at boot but then when i go boot from a DVD it says to load the kernel first and either the partition is found or it cant find the /s/c of the hard drive or something... Can anbody shed some light on this?

---

### Post by sisco311 on 2010-03-26
Grub2 counts the first drive as 0 & the first partition as 1: (hd0,1).

---

### Post by prodigy_ on 2010-03-26
> **sisco311 said:**
> Grub2 counts the first drive as 0 & the first partition as 1
```
Grub2 != consistency
```
/sigh

---

### Post by lvalen18 on 2010-03-26
But it should boot DVD even though i had it as (hd0,0) that how it was on legacy.. and so you know i added numbers to it... i tried hd1,0 and hd0,1 so on an so fourth to see if it made a difference.. but nope still same thing

---

### Post by sisco311 on 2010-03-26
[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

[thread=1288604]HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2[/thread]

---

