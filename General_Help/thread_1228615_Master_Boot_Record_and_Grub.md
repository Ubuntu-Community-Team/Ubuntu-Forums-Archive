---
title: "Master Boot Record and Grub"
date: 2009-08-01
forum: General Help
---

### Post by ineedshelp on 2009-08-01
Hello,

I just installed Dreamlinux onto my computer that already had Ubuntu, Linux Mint and Windows Vista. When it installed the grub splash screen changed from Linux Mint to Dreamlinux. It said something about writting the bootloader to my Master Boot Record. What I am asking is this: is there any way to change the grub menu screen image and what does it mean when it writes grub to my MBR (can it be edited/undone by deleting the Dreamlinux partition)?

Thanks.

---

### Post by theozzlives on 2009-08-01
The Boot Strap Program in the BIOS looks to the MBR (Master Boot Record) of your boot device, then loads the Boot Loader (GRUB, LILO, Windows, etc.), which loads the OS, to put it simply. You can re-write your MBR.

---

### Post by ncmncm on 2009-08-01
I think you need to look into  your GRUB menu file. 
On my laptop running just Ubuntu, I can edit the GRUB menu here:

```
/boot/grub/menu.lst
```


Looks like the new installation has modified your MBR.

---

### Post by ineedshelp on 2009-08-01
How can  I re-write my MBR?

---

