---
title: "How to create bootable dos, or winnt, floppy?"
date: 2011-08-18
forum: General Help
---

### Post by LinUxaliVe on 2011-08-18
Hello. Could someone help me out with a questions relating to creating floppy images?

I've created an empty floppy image that I would later like to add boot files to, and mounted it, with these commands.

```
dd bs=512 count=1440 if=/dev/zero of=/floppy.ima
mkfs.msdos /floppy.ima
mkdir /mnt/vfloppy
mount -o loop /floppy.ima /mnt/vfloppy
```The problem? Using this method instead of say formatting the floppy image in Windows, I have no 'boot code'.

This would normally be creating under a format in Win9x, or WinNT, based OSes when a floppy (or floppy image) is formatted.

Are there any base Linux utilities, or packages, that will add the DOS/NT boot code info to floppy images. Thereby making them bootable in DOS/Win9x/WinNT environments...

---

### Post by An Sanct on 2011-08-19
I know, this does not answer your question, but I tried to attached a compressed dos boot image file, but it was 1.07Mb, which is clearly over the attachment limit of 967kb ;)

The boot sector and system files are proprietary, maybe that is why you did not find a Linux tool to create a MS dos boot image. Give free dos a try, that is free.

---

