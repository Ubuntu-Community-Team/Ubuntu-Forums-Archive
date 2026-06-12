---
title: "Permission denied even with root user"
date: 2011-12-26
forum: General Help
---

### Post by edu2004eu on 2011-12-26
My Windows 7 recently crashed so I switched to Ubuntu 11. Ubuntu sees my windows partition, I am able to access the files on it (read, edit, delete), except for a folder (an important one). I can't even read the files in there or back them up. It gives me a "permission denied" error when opening even text files. I've tried with ```
sudo nano bla.txt
``` but that gave me an empty file.

```
ls -l
``` returns this:
```
total 744
-rw------- 1 edy edy      6 2011-12-14 17:41 bla.txt
-rw------- 1 edy edy  22212 1992-06-10 03:10 DPMILOAD.EXE
-rw------- 1 edy edy  24932 1992-06-10 03:10 DPMIMEM.DLL
-rw------- 1 edy edy    231 2011-12-08 08:53 lab1.asm
-rw------- 1 edy edy    469 2011-12-14 17:36 lab.asm
-rw------- 1 edy edy    602 2011-12-14 17:40 LAB.EXE
-rw------- 1 edy edy    195 2011-12-14 17:40 LAB.MAP
-rw------- 1 edy edy    278 2011-12-14 17:40 LAB.OBJ
-rw------- 1 edy edy 133580 2011-11-06 20:32 TASM.EXE
-rw------- 1 edy edy    807 2011-12-11 20:53 TDCONFIG.TD
-rw------- 1 edy edy 487136 2011-11-06 20:32 TD.EXE
-rw------- 1 edy edy  53510 2011-11-06 20:32 TLINK.EXE
```

All have read + write for the owner. When I tried to CHMOD them, chmod returned no error, but didn't do anything either.

Could anyone help me with this? Thank you!

---

### Post by llamabr on 2011-12-26
What's up with this "special" file?  was it encrypted, or otherwise strangely FS'd?

---

### Post by Habitual on 2011-12-26
```

sudo nano /path/to/bla.txt

```

---

### Post by edu2004eu on 2011-12-26
> **llamabr said:**
> What's up with this "special" file?  was it encrypted, or otherwise strangely FS'd?

No, not encrypted or other stuff done to it. and it's not only that file, it's the whole directory.

Although (not sure if it matters), in Windows 7 the name of the directory was colored with green, which I just googled, and it means that indeed the folder was encrypted, but I didn't do it, so not sure why. So is there any way I can decrypt it?

Thanks!

---

