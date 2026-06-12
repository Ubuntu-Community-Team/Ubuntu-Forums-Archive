---
title: "What do i do with this file?"
date: 2010-06-20
forum: General Help
---

### Post by megamandos on 2010-06-20
Ok, so i got this stuff for a patch and I dont know what to do with it. The files I have are from this post: [http://ubuntuforums.org/showthread.php?t=1369224](http://ubuntuforums.org/showthread.php?t=1369224)

The file in questions is this one:

(patch_dmraid-1.0.0.rc16.txt)
```
Only in dmraid_patch/1.0.0.rc16: config.log
Only in dmraid_patch/1.0.0.rc16: config.status
diff -r dmraid/1.0.0.rc16/configure.in dmraid_patch/1.0.0.rc16/configure.in
24a25,26
> AC_CHECK_LIB([parted])
> 
Only in dmraid_patch/1.0.0.rc16/include/dmraid: .metadata.h.swp
Only in dmraid_patch/1.0.0.rc16/include: Makefile
diff -r dmraid/1.0.0.rc16/lib/format/ondisk.h dmraid_patch/1.0.0.rc16/lib/format/ondisk.h
24a25
> #include "partition/part.h"
diff -r dmraid/1.0.0.rc16/lib/format/partition/dos.c dmraid_patch/1.0.0.rc16/lib/format/partition/dos.c
193a194
>     log_notice(lc, "%s: partition offset:%ull sectors:%ull", handler, r->offset, r->sectors);
Only in dmraid_patch/1.0.0.rc16/lib/format/partition: gpt.old.c
Only in dmraid_patch/1.0.0.rc16/lib/format/partition: part.c
Only in dmraid_patch/1.0.0.rc16/lib/format/partition: part.h
diff -r dmraid/1.0.0.rc16/lib/format/register.h dmraid_patch/1.0.0.rc16/lib/format/register.h
31c31,32
<     xx(dos)
---
> //    xx(dos)
>         xx(part)
diff -r dmraid/1.0.0.rc16/lib/format/template/template.c dmraid_patch/1.0.0.rc16/lib/format/template/template.c
200a201
>     .destroy = NULL,
Only in dmraid_patch/1.0.0.rc16/lib: Makefile
diff -r dmraid/1.0.0.rc16/lib/Makefile.in dmraid_patch/1.0.0.rc16/lib/Makefile.in
46c46,47
<     format/partition/dos.c
---
>     format/partition/dos.c \
>     format/partition/part.c
Only in dmraid_patch/1.0.0.rc16: Makefile
Only in dmraid_patch/1.0.0.rc16: make.tmpl
diff -r dmraid/1.0.0.rc16/make.tmpl.in dmraid_patch/1.0.0.rc16/make.tmpl.in
19c19
< LDFLAGS += @LDFLAGS@
---
> LDFLAGS += @LDFLAGS@ -lparted
Only in dmraid_patch/1.0.0.rc16/man: Makefile
Only in dmraid_patch/1.0.0.rc16/tools: libdmraid.so.1.0.0.rc16
Only in dmraid_patch/1.0.0.rc16/tools: Makefile
Only in dmraid_patch/1.0.0.rc16/tools: version.h
```

To me, it looks like it needs to be run as a script or something, but i have no idea how... ::confused:

---

