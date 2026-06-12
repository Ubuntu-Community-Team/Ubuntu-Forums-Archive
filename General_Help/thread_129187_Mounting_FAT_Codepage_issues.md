---
title: "Mounting FAT: Codepage issues"
date: 2006-02-13
forum: General Help
---

### Post by el3ktro on 2006-02-13
I ran into the same problem again:

I have a FAT partition, used within a German Windows XP. The files have letters like "ä ö ü" (German umlauts) inside. Those are displayed fine within Windows XP. When I mount this partition in Ubuntu (mount -t vfat -o uid=1000,gid=1000,umask=027) Gnome doesn't print those umlauts correctly, it "extends" the filename with the words (invalid encoding).

mount.vfat uses coeepage 437 as default, I've also tried codepage=850 which doesn't help, utf8 or utf-8 are not supported. When I rename the file within Gnome so that it displays correctly in Gnome, then it doesn't look right in Windows again.

I really need to fix this - is there any way to get around this? What else could I do?


Tom

---

### Post by frodon on 2006-02-13
i had the same problem but even if gnome don't display the file correctly you will be able to use it.
In my case i wrote a small script to rename the needed files.

---

### Post by jazzgossen on 2006-02-13
Try adding "iocharset=iso8859-1,utf8" to the mount options (or to the options field in /etc/fstab, if you want).

---

### Post by GTvulse on 2006-02-13
[QUOTE=jazzgossen]Try adding "iocharset=iso8859-1,utf8" to the mount options (or to the options field in /etc/fstab, if you want).[/QUOTE]

[FONT="Courier New"]iocharset=cp850,utf8[/FONT] works much better. There is no one-to-one correspondence between ISO-8859-1 and CP850, and the latter is the encoding used by WinXP's DOS emulation in versions localized to Western European languages. Just don't use Euro signs in filenames...

---

### Post by el3ktro on 2006-02-13
Hello!

Thanks, putting iocharset=utf8 into /etc/fstab solved the problem, it works perfectly now!

Tom

---

