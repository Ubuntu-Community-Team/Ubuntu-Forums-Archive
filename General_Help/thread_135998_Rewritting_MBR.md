---
title: "Rewritting MBR"
date: 2006-02-25
forum: General Help
---

### Post by alamba on 2006-02-25
Is there a way to re-write the MBR using ubuntu live cd or the installation cd? I'm looking for a "ubuntu way" of doing fdisk /mbr in the "old dos way".

The desire here is to first clean out the MBR and then re-write/re-install grub on it.

Akshay

---

### Post by Trab on 2006-02-25
ummm...
try running the rescue option on the ubuntu install disk...
when u get to a prompt, type ```
 grub-install /dev/hda1 
```
not sure wat u need to do, but that will install grub for you...:-/

---

### Post by heimo on 2006-02-25
[quote=alamba]The desire here is to first clean out the MBR and then re-write/re-install grub on it.[/quote] If that's literally what you want to do, then this should write all zeros over your master boot record on device hda. (If anyone who is reading this doesn't know what (s)he's doing, don't do it.) Behaviour is not the same as *fdisk /mbr* in Windows.
```
dd if=/dev/zero of=/dev/hda bs=512 count=1
``` You need to add *sudo* in front of this comman and replace hda with the actual device you want to use.

---

### Post by alamba on 2006-02-25
Trab: Thanks. But that would only install/reinstall grub. Not clean out the MBR.

Heimo: As you pointed out, behaviour is not the same as fdisk /mbr. Anyway to extract that behaviour? If I do as you suggest on a dual boot system would windows still be able to boot? I need to be extra carefull on this system since its not my personal machine.

A

---

### Post by heimo on 2006-02-25
No it will not boot. You need to use Microsoft fdisk or if you have copy of mbr, you can use dd to copy it back to master boot record using dd. Use Windows boot disk, or boot cd to use their fdisk. But if your goal is to overwrite it with grub, I have no idea why this step would be neccessary.

If you want to save the current mbr, overwrite it and then restore using Ubuntu, you can:
```
dd if=/dev/hda of=mbr.img bs=512 count=1
``` to save (backup mbr.img file to safe place)

----------------------

```
dd if=mbr.img of=/dev/hda bs=512 count=1
``` to restore


I give no guarantee that this will work in your situation. Always backup any valuable data before doing changes like this.

---

### Post by alamba on 2006-02-25
Cool, thanks!

---

### Post by Toet on 2007-12-25
dd if=/dev/zero of=/dev/hda bs=512 count=1


DO NOT try this one. Overwriting the first 512 blocks will whipe your partition table aswell, not only the mbr!!

---

### Post by LaRoza on 2007-12-25
If you want to rewrite the MBR (for Windows and others) you can use the Super Grub Disk. See the link in my sig.

---

### Post by Gen2ly on 2007-12-25
Here's a good wiki on it:

[GLW - MBR]("http://gentoo-wiki.com/MBR")

---

