---
title: "Why can't I execute this program?"
date: 2009-12-18
forum: General Help
---

### Post by fark0 on 2009-12-18
I just downloaded a program, fwNES (the program itself is not important), and this happens. Why?!

[IMG]http://i46.tinypic.com/28gy42q.png[/IMG]

---

### Post by blueridgedog on 2009-12-18
From the same location, what is the output of:

```
file ./fwnes
```

If it is a shell script, it may have a bad path to the interpreter at the top, or a shell called for that you don't have.

---

### Post by pbrane on 2009-12-18
```

**file ./fwnes**
./fwnes: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), **dynamically linked** (uses shared libs), not stripped


**ldd fwnes**
	not a **dynamic executable**

```

Interesting. It is an old program, 1998. Uses SVGALIB. You need to run it as root, but I don't think SVGALIB is supported anymore.

---

### Post by caleb_yau on 2009-12-18
oh man i totally have a hella similar issue. checkout [http://ubuntuforums.org/showthread.php?t=1358824](http://ubuntuforums.org/showthread.php?t=1358824)

---

### Post by fark0 on 2009-12-18
Thanks you guys. I guess it's SVAGLIB or the lack of it that it causing this. I will find a different emulator. :)

---

