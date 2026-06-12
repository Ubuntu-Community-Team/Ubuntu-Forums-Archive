---
title: "Brutfir : ISO C90 does not support long long...."
date: 2012-08-06
forum: General Help
---

### Post by Gusss on 2012-08-06
Im quite new to linux but Im trying to install Brutefir :

[http://www.ludd.luth.se/~torger/brutefir.html](http://www.ludd.luth.se/~torger/brutefir.html)

 to work with an audio program called wonder. Something called "long long" appears to be a problem - Id be most grateful if you could tell me what I need to do to compile it :

```

    gcc -o dai.o            -c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 dai.c
    In file included from dai.c:25:0:
    defs.h:16:23: warning: ISO C90 does not support ‘long long’
    defs.h:17:14: warning: ISO C90 does not support ‘long long’
    flex -obfconf_lexical.c bfconf_lexical.lex
    make: flex: Command not found
    make: *** [bfconf_lexical.c] Error 127

```


cheers,
Augustine Leudar

full readout :

```
dew@dew-PA65-UD3-B3:~/Desktop/brutefir-1.0k$ make
gcc -o brutefir.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 brutefir.c
In file included from bfconf.h:13:0,
                 from brutefir.c:16:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
gcc -o fftw_convolver.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 fftw_convolver.c
In file included from fftw_convolver.c:7:0:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
In file included from fftw_convolver.c:160:0:
raw2real.h: In function ‘raw2realf’:
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
In file included from fftw_convolver.c:181:0:
raw2real.h: In function ‘raw2reald’:
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
In file included from fftw_convolver.c:467:0:
real2raw.h: In function ‘real2rawf_hp_tpdf’:
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
In file included from fftw_convolver.c:476:0:
real2raw.h: In function ‘real2rawf_no_dither’:
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
real2raw.h:86:58: warning: use of C99 long long integer constant
In file included from fftw_convolver.c:490:0:
real2raw.h: In function ‘real2rawd_hp_tpdf’:
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
In file included from fftw_convolver.c:499:0:
real2raw.h: In function ‘real2rawd_no_dither’:
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
real2raw.h:118:60: warning: use of C99 long long integer constant
gcc -o bfconf.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 bfconf.c
In file included from bfconf.c:7:0:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
In file included from bfconf.c:1779:0:
raw2real.h: In function ‘raw2realf’:
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
raw2real.h:45:58: warning: use of C99 long long integer constant
In file included from bfconf.c:1785:0:
raw2real.h: In function ‘raw2reald’:
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
raw2real.h:76:60: warning: use of C99 long long integer constant
bfconf.c: In function ‘bfconf_init’:
bfconf.c:2998:42: warning: new qualifiers in middle of multi-level non-const cast are unsafe
gcc -o bfrun.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 bfrun.c
In file included from bfrun.c:7:0:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
bfrun.c: In function ‘test_silent’:
bfrun.c:730:11: warning: declaration of ‘fmax’ shadows a global declaration
bfrun.c: In function ‘bfrun’:
bfrun.c:2445:8: warning: new qualifiers in middle of multi-level non-const cast are unsafe
bfrun.c:2479:8: warning: new qualifiers in middle of multi-level non-const cast are unsafe
bfrun.c: In function ‘bflogic_names’:
bfrun.c:2688:5: warning: new qualifiers in middle of multi-level non-const cast are unsafe
bfrun.c: In function ‘bfio_names’:
bfrun.c:2714:5: warning: new qualifiers in middle of multi-level non-const cast are unsafe
gcc -o firwindow.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 firwindow.c
In file included from firwindow.h:10:0,
                 from firwindow.c:11:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
gcc -o emalloc.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 emalloc.c
In file included from emalloc.c:12:0:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
gcc -o shmalloc.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 shmalloc.c
In file included from shmalloc.c:7:0:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
gcc -o dai.o			-c -I/usr/local/include -Wall -Wlong-long -Wpointer-arith -Wshadow -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -O2 dai.c
In file included from dai.c:25:0:
defs.h:16:23: warning: ISO C90 does not support ‘long long’
defs.h:17:14: warning: ISO C90 does not support ‘long long’
flex -obfconf_lexical.c bfconf_lexical.lex
make: flex: Command not found
make: *** [bfconf_lexical.c] Error 127

```

---

