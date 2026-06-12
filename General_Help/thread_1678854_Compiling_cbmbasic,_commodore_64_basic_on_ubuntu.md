---
title: "Compiling cbmbasic, commodore 64 basic on ubuntu"
date: 2011-01-31
forum: General Help
---

### Post by afrodeity on 2011-01-31
```

svn co https://cbmbasic.svn.sourceforge.net/svnroot/cbmbasic cbmbasic


```

```

make
cc -Wall -O3   -c -o cbmbasic.o cbmbasic.c
cc -Wall -O3   -c -o runtime.o runtime.c
runtime.c: In function &#8216;OPEN&#8217;:
runtime.c:294: warning: pointer targets in passing argument 1 of &#8216;fopen&#8217; differ in signedness
/usr/include/stdio.h:269: note: expected &#8216;const char * __restrict__&#8217; but argument is of type &#8216;unsigned char *&#8217;
cc -Wall -O3   -c -o plugin.o plugin.c
plugin.c: In function &#8216;plugin_gone&#8217;:
plugin.c:265: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
cc -o cbmbasic cbmbasic.o runtime.o plugin.o
runtime.o: In function `kernal_dispatch':
runtime.c:(.text+0xefb): undefined reference to `get_cursor'
runtime.c:(.text+0x18a1): undefined reference to `set_color'
runtime.c:(.text+0x18b2): undefined reference to `set_color'
runtime.c:(.text+0x18c1): undefined reference to `left_cursor'
runtime.c:(.text+0x18d5): undefined reference to `set_color'
runtime.c:(.text+0x18e6): undefined reference to `set_color'
runtime.c:(.text+0x18fd): undefined reference to `set_color'
runtime.c:(.text+0x190e): undefined reference to `set_color'
runtime.c:(.text+0x191f): undefined reference to `set_color'
runtime.o:runtime.c:(.text+0x1930): more undefined references to `set_color' follow
runtime.o: In function `kernal_dispatch':
runtime.c:(.text+0x1961): undefined reference to `clear_screen'
runtime.c:(.text+0x1971): undefined reference to `up_cursor'
runtime.c:(.text+0x1985): undefined reference to `set_color'
runtime.c:(.text+0x1996): undefined reference to `set_color'
runtime.c:(.text+0x19bc): undefined reference to `set_color'
runtime.c:(.text+0x19cd): undefined reference to `set_color'
runtime.c:(.text+0x19d7): undefined reference to `right_cursor'
runtime.c:(.text+0x19f1): undefined reference to `set_color'
runtime.c:(.text+0x1a0a): undefined reference to `move_cursor'
runtime.c:(.text+0x1a16): undefined reference to `down_cursor'
runtime.c:(.text+0x1a5c): undefined reference to `set_color'
plugin.o: In function `plugin_gone':
plugin.c:(.text+0x4e1): undefined reference to `move_cursor'
collect2: ld returned 1 exit status
make: *** [cbmbasic] Error 1

```

Any ideas?

---

### Post by [Snc] on 2011-01-31
> **afrodeity said:**
> ```

svn co https://cbmbasic.svn.sourceforge.net/svnroot/cbmbasic cbmbasic


``````

make
cc -Wall -O3   -c -o cbmbasic.o cbmbasic.c
cc -Wall -O3   -c -o runtime.o runtime.c
runtime.c: In function &#8216;OPEN&#8217;:
runtime.c:294: warning: pointer targets in passing argument 1 of &#8216;fopen&#8217; differ in signedness
/usr/include/stdio.h:269: note: expected &#8216;const char * __restrict__&#8217; but argument is of type &#8216;unsigned char *&#8217;
cc -Wall -O3   -c -o plugin.o plugin.c
plugin.c: In function &#8216;plugin_gone&#8217;:
plugin.c:265: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
cc -o cbmbasic cbmbasic.o runtime.o plugin.o
runtime.o: In function `kernal_dispatch':
runtime.c:(.text+0xefb): undefined reference to `get_cursor'
runtime.c:(.text+0x18a1): undefined reference to `set_color'
runtime.c:(.text+0x18b2): undefined reference to `set_color'
runtime.c:(.text+0x18c1): undefined reference to `left_cursor'
runtime.c:(.text+0x18d5): undefined reference to `set_color'
runtime.c:(.text+0x18e6): undefined reference to `set_color'
runtime.c:(.text+0x18fd): undefined reference to `set_color'
runtime.c:(.text+0x190e): undefined reference to `set_color'
runtime.c:(.text+0x191f): undefined reference to `set_color'
runtime.o:runtime.c:(.text+0x1930): more undefined references to `set_color' follow
runtime.o: In function `kernal_dispatch':
runtime.c:(.text+0x1961): undefined reference to `clear_screen'
runtime.c:(.text+0x1971): undefined reference to `up_cursor'
runtime.c:(.text+0x1985): undefined reference to `set_color'
runtime.c:(.text+0x1996): undefined reference to `set_color'
runtime.c:(.text+0x19bc): undefined reference to `set_color'
runtime.c:(.text+0x19cd): undefined reference to `set_color'
runtime.c:(.text+0x19d7): undefined reference to `right_cursor'
runtime.c:(.text+0x19f1): undefined reference to `set_color'
runtime.c:(.text+0x1a0a): undefined reference to `move_cursor'
runtime.c:(.text+0x1a16): undefined reference to `down_cursor'
runtime.c:(.text+0x1a5c): undefined reference to `set_color'
plugin.o: In function `plugin_gone':
plugin.c:(.text+0x4e1): undefined reference to `move_cursor'
collect2: ld returned 1 exit status
make: *** [cbmbasic] Error 1

```Any ideas?

Oh yeah ... does your compiler meet the minimum? 
(GCC 3.3/4.1)

(C64 fan here ;))

---

### Post by afrodeity on 2011-01-31
```


gcc --version
gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

minimum or maximum?

---

### Post by [Snc] on 2011-01-31
> **afrodeity said:**
> ```


gcc --version
gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```minimum or maximum?

hm ... good question :} maybe there is a large difference between 4.1 and 4.4, but not large enough, to call it 5.0 for example ....

What does the line of code, where the error is reported say?

---

