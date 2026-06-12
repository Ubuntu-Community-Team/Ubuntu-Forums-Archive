---
title: "Help fixing my DSDT bugs"
date: 2009-09-19
forum: General Help
---

### Post by HolyShnikes on 2009-09-19
I have been looking for the past 2 hours and I can't find the solutions to my errors and warnings for my DSDT.  I don't know if I am searching wrong or something, but I just can't seem to get it.  I am running Ubuntu 9.04 on my HP dV6704nr Laptop.

If you can help please, I really need it.  Thanks.


```

nathan@ubuntu:~$ iasl -tc /home/nathan/dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/nathan/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -                              ^ Reserved method must return a value (_WAK)

/home/nathan/dsdt.dsl  3535:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -    Not all control paths return a value ^  (_Q16)

/home/nathan/dsdt.dsl  7709:                 Method (_HOT, 0, Serialized)
Warning  1087 -    Not all control paths return a value ^  (_HOT)

/home/nathan/dsdt.dsl  7709:                 Method (_HOT, 0, Serialized)
Warning  1080 -     Reserved method must return a value ^  (_HOT)

/home/nathan/dsdt.dsl  7711:                     Zero
Error    4095 -                                     ^ syntax error, unexpected PARSEOP_ZERO

/home/nathan/dsdt.dsl  7718:                 Method (_CRT, 0, Serialized)
Warning  1087 -    Not all control paths return a value ^  (_CRT)

/home/nathan/dsdt.dsl  7718:                 Method (_CRT, 0, Serialized)
Warning  1080 -     Reserved method must return a value ^  (_CRT)

/home/nathan/dsdt.dsl  7720:                     Zero
Error    4095 -                                     ^ syntax error, unexpected PARSEOP_ZERO

ASL Input:  /home/nathan/dsdt.dsl - 8126 lines, 278510 bytes, 4166 keywords
Compilation complete. 2 Errors, 6 Warnings, 0 Remarks, 1126 Optimizations
```

---

### Post by HolyShnikes on 2009-09-20
*bump*

---

### Post by anonymous_user on 2009-09-20
[Post in this thread](http://ubuntuforums.org/showthread.php?t=1036051), 67GTA can help you.

---

