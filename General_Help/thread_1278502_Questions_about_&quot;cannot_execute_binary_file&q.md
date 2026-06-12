---
title: "Questions about &quot;cannot execute binary file&quot;"
date: 2009-09-29
forum: General Help
---

### Post by aquar on 2009-09-29
Dear all:

I downloaded a pre-released programme mach1 from this link below for study&#65306;
[http://www.sph.umich.edu/csg/abecasis/MACH/download/](http://www.sph.umich.edu/csg/abecasis/MACH/download/)

and then unzipped it to /home/aquar/mach. However, when I tried to run 
the program using "./mach1", the result is
"bash: cannot execute binary file"

I thought maybe the file is corrupted, so I contacted the programmer. She replied soon with the answer "Ah, the executable is under the executable/ folder. Use ./executable/mach1 ". But I never found the folder executable in Ubuntu 8.04 (on my computer), and of course the result wass "bash: No such file or directory" when I tried to use ./executable/mach1.

Any clues?:confused: Your ideas are greatly appreciated!

Thank you very much:)

---

### Post by diesch on 2009-09-29
It's indeed ./mach1, but the program is only for x86-64. I guess you are running on i386

---

### Post by aquar on 2009-09-29
True...
A simple question: How do you know the program is only for x86-64? I mean, which command do you use? I doubted that but I did not know how to get the information.

Sorry I am kind of new to Linux, so many thanks for your help:-)

---

### Post by diesch on 2009-09-29
"file" is a simple way to get some information about a file:
```

$ file mach1 
mach1: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.0, not stripped

$ file /bin/true
/bin/true: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped

```It works for most other common file types, too, e.g.
```

$ file test.dat
test.dat: PNG image, 1064 x 1645, 8-bit/color RGB, non-interlaced

```

---

### Post by aquar on 2009-09-29
Thank you!

---

