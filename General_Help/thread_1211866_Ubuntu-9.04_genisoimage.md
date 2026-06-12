---
title: "Ubuntu-9.04 genisoimage"
date: 2009-07-13
forum: General Help
---

### Post by fouad_jh on 2009-07-13
Hi folks, I am trying to build live CD, when I try to generate the iso image using genisoimage I get an error, I am just copying the command from the live cd customization, here is the command I issue and the error message:

user1@LABUbuntu:/media/Data/live/extract-cd$ sudo mkisofs -D -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-9.04.1-desktop-i386-custom.iso
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Use genisoimage -help
to get a list of valid options.

Report problems to [email]debburn-devel@lists.alioth.debian.org[/email].
user1@LABUbuntu:/media/Data/live/extract-cd$

---

### Post by fouad_jh on 2009-07-13
Sorry guys, I just solved it, it was the "." at the end of the command, for the destination folder, I though it was just end of line "."

Cheers

---

### Post by seshagiri on 2010-01-13
The actual code contains a 'space' and '.' at the end
> **sudo mkisofs -D -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-9.04.1-desktop-i386-custom.iso .**

---

