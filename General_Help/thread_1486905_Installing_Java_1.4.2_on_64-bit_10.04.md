---
title: "Installing Java 1.4.2 on 64-bit 10.04"
date: 2010-05-18
forum: General Help
---

### Post by txmxmatt on 2010-05-18
Does anyone have any pointers on installing java 1.4.2 JDK on 64-bit 10.04? I can't seem to find a whole lot about this anywhere. I've tried downloading the .bin from  sun's archive site [java.sun.com/products/archive] but I get this error when running it:

> Unpacking...
Checksumming...
0
0
Extracting...
./j2sdk-1_4_2_19-linux-i586.bin: 442: ./install.sfx.3866: not found
Done.

Thanks in advance.

---

### Post by bouncysteve on 2010-09-22
Install the ia32-libs package to run 32bit programs on 64 bit:

```
sudo apt-get install ia32-libs
```

I had the same problem and this fixed it.

---

