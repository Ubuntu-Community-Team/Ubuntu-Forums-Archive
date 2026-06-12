---
title: "Quick Question"
date: 2009-08-21
forum: General Help
---

### Post by moobie1992 on 2009-08-21
If I install Ubuntu on a external HD. Can I take that HD and plug it into any computer and it "should" ask if I want to boot to Ubuntu right?

---

### Post by bchurchill on 2009-08-21
More or less, yes, it should.

When your computer starts it runs a program called BIOS which searches for all things it could boot from.  Usually it will boot to the first hard drive or to a CD rom.  However, there's also a boot menu where you choose which hard drive to boot from.  When you first turn on the computer it will probably display a button to press to get to the boot menu.  Often it's F10, F11 or F12.  Then you can select which hard drive you want to boot from.  However, it almost definitely won't identify the hard drive as Ubuntu, you'll need to figure out which one is which (it'll probably be pretty obvious though)

If your BIOS isn't new enough to recognize your external hard drive, it might not work.  This is more likely to be a problem with USB external drives on older computers, but shouldn't be an issue on a modern system.

---

### Post by moobie1992 on 2009-08-21
Thanks bchurchill, you just saved me a lot of money.

---

### Post by neophyte_7 on 2009-08-21
You might also have to put in hte right numbers for booting from external,
inthe menu.lst file in /boot/grub inorder for grub to recognize the new partition I guess....

---

