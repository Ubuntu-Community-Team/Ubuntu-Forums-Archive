---
title: "error trying to compile PCSX, &quot;No package 'gtk+-2.0' found&quot;"
date: 2006-05-04
forum: General Help
---

### Post by JacksonL on 2006-05-04
I'm trying to build PCSX 1.5 from source. ./configure works perfectly, but when I try to make it gives me the following error (truncated because it's really really long and repetitive):
```

jackson@jacksonLeonard:~/Desktop/PcsxSrc-1.5/Linux$ make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc -Wall -O4 -fomit-frame-pointer -finline-functions -ffast-math -fno-exception s -march=pentiumpro -I. -I.. -D__LINUX__ -DPCSX_VERSION=\"1.5\" -DPACKAGE=\"pcsx \" -DENABLE_NLS -D__i386__  -c -o ../PsxBios.o ../PsxBios.c
../PsxBios.c: In function ‘psxBios_atoi’:
../PsxBios.c:308: warning: null argument where non-null required (argument 1)
../PsxBios.c: In function ‘psxBios_atol’:
../PsxBios.c:313: warning: null argument where non-null required (argument 1)
../PsxBios.c: In function ‘psxBios_strcat’:
../PsxBios.c:358: warning: null argument where non-null required (argument 1)
../PsxBios.c:358: warning: null argument where non-null required (argument 2)
../PsxBios.c:358: warning: null argument where non-null required (argument 1)
../PsxBios.c:358: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘psxBios_strncat’:
../PsxBios.c:362: warning: null argument where non-null required (argument 1)
../PsxBios.c:362: warning: null argument where non-null required (argument 2)

```

After that it just continues going on with the "null argument" things. If posting that would help you guys help me then I'd be more than glad to. Thanks! :-({|=

---

### Post by JacksonL on 2006-05-05
well if nobody can help me, can you guys at least tell me how to edit that environment variable so I can fiddle with it?

---

### Post by orlox on 2006-05-05
did you install gtk+. If not, install it with synaptic...

---

### Post by JacksonL on 2006-05-07
I'm pretty sure I have it installed. I mean, I'm running GNOME perfectly well. I also get this error when trying to compile mupen64.

---

