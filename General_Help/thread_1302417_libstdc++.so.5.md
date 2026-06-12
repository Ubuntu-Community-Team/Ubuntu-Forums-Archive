---
title: "libstdc++.so.5?"
date: 2009-10-27
forum: General Help
---

### Post by DejitaruJin on 2009-10-27
I'm trying to run a program (Realflow), and it gives an error:
```
/usr/realflow/bin/realflow.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```Like most people who have had this problem, I installed the libstdc++5 package. In fact, I've installed several packages that may be even remotely helpful in this matter. However, that's where there is a problem. You see, in every single case I've seen, dating back to 2005, this fixes the problem. In my case, despite the file being exactly where it ought to be, the program still can not find it. As best I can tell, this is either a Karmic problem, or the program isn't looking in the right place. Does anyone know how I can confirm or dismiss either?

---

### Post by rockstarrem on 2009-10-27
I got your problem and this seemed to fix it:

```

ldconfig

```

---

### Post by DejitaruJin on 2009-10-27
I'm not entirely sure what that would do, but it didn't fix it.

EDIT: I went about creating symlinks anywhere I could think of. The last place I tried was in its own lib folder. The result? It found the file... it just wasn't apparently what it was looking for at all.

```
/usr/realflow/bin/realflow.bin: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS64

```

---

### Post by DejitaruJin on 2009-10-27
For anyone who finds this topic through a search, the issue is I was trying to use a 32-bit app on a 64-bit system, with 64-bit libraries. PEBKAC.

In this instance, the program was looking in the /lib32 directory for the missing file. After manually extracting the 32-bit libraries from a deb file and putting them there, everything ran perfectly.

---

