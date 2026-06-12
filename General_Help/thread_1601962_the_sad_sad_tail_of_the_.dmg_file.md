---
title: "the sad sad tail of the .dmg file"
date: 2010-10-20
forum: General Help
---

### Post by Mergular on 2010-10-20
Hi, Im trying to open a .dmg file but when I type file filename.dmg it says:
/home/user/filename.dmg: data
it used to say:
/home/user/filename.dmg:  VAX COFF executable not stripped – version 376
how do I get it to say that again :(?
 P.S. I used vfdecrypt to decrypt the .dmg file

---

### Post by srs5694 on 2010-10-21
If this is a disk image file such as created on a Mac, then the identification of the file as a VAX COFF executable was in error. Probably the file just randomly included the string that the "file" utility uses to identify VAX COFF files, resulting in a false alarm detection.

If you need to positively identify .dmg files, you may need to investigate how to do so and then update the /usr/share/misc/magic.mgc file. I'm afraid I can't offer much advice on how to do this, though, but doing Web searches on relevant terms might get you started on finding out how to do it. Reading the man page and any other documentation you can find on "file" is also worth doing.

---

