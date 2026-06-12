---
title: "gdb compiling error"
date: 2010-01-05
forum: General Help
---

### Post by shariefbe on 2010-01-05
When i compiling gdb for ARM processor i am getting this error as
```

checking for iconv declaration... install-shextern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for library containing waddstr... no
configure: WARNING: no enhanced curses library found; disabling TUI
checking for library containing tgetent... no
configure: error: no termcap library found
make[1]: *** [configure-gdb] Error 1
make[1]: Leaving directory `/mnt/freescale/sources/gdb-7.0'
make: *** [all] Error 2
sharief@sharief-desktop:/mnt/freescale/sources/gdb-7.0$ 

```
can anyone tell me what will be the error. I think th termcap library is not there. i downloaded and cross compiled tremcap library but still it is not working. kindly help me

---

