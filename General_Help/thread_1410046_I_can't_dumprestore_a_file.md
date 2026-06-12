---
title: "I can't dump/restore a file?"
date: 2010-02-18
forum: General Help
---

### Post by Vladimir Hidalgo on 2010-02-18
Hi!, I got a backup file which first 1000 bytes are as follows:

```
[SIZE="2"]00000000  54 41 50 45 00 00 03 00  8c 00 0e 01 00 00 00 00  |TAPE............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  02 00 87 05 51 64 50 48  01 00 00 00 01 00 00 00  |....QdPH........|
00000040  01 00 01 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  2c 00 5e 00 00 04 00 12  1f 68 90 e7 f3 01 4d 00  |,.^......h....M.|
00000060  69 00 63 00 72 00 6f 00  73 00 6f 00 66 00 74 00  |i.c.r.o.s.o.f.t.|
00000070  20 00 53 00 51 00 4c 00  20 00 53 00 65 00 72 00  | .S.Q.L. .S.e.r.|
00000080  76 00 65 00 72 00 00 00  00 00 00 00 53 50 41 44  |v.e.r.......SPAD|
00000090  00 00 00 00 5e 03 00 00  00 00 00 00 00 00 00 00  |....^...........|
000000a0  4c 17 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |L...............|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000003e0  00 00 00 00 00 00 00 00                           |........|
[/SIZE]
```

I tried to restore it:
```
$ restore -r -f zzz_labxxxx
Checksum error 32615101403, inode 0 file (null)
restore: **Tape is not a dump tape**
```

What application could I use or even try? The man who made the backup can't be reached anymore and we had been left with the backup.

Thanks for any help.

---

### Post by gmargo on 2010-02-18
Does the **file** command recognize the format of zzz_labxxxx?  It sort of looks like a **tar** image to me.

---

