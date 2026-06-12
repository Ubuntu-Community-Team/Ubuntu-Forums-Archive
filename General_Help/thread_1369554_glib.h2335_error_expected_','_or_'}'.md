---
title: "glib.h:2335: error: expected ',' or '}'"
date: 2010-01-01
forum: General Help
---

### Post by shariefbe on 2010-01-01
hello when i try to compile pkg-config.it shows error as 
```

fp -mfpu=vfp3 -ftree-vectorize -funroll-all-loops -Wall -D_REENTRANT -MT garray.lo -MD -MP -MF .deps/garray.Tpo -c garray.c  -fPIC -DPIC -o .libs/garray.o
In file included from garray.c:32:
glib.h:2335: error: expected ',' or '}' before 'GLIB_SYSDEF_POLLIN'
make[2]: *** [garray.lo] Error 1
make[2]: Leaving directory `/mnt/freescale/sources/pkg-config-0.20/glib-1.2.8'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/mnt/freescale/sources/pkg-config-0.20/glib-1.2.8'
make: *** [all] Error 2
sharief@sharief-desktop:/mnt/freescale/sources/pkg-config-0.20/glib-1.2.8$ vim glib.h 


```
This the glib.h file

```

 */

typedef struct _GIOFuncs GIOFuncs;
typedef enum
{
  G_IO_ERROR_NONE,
  G_IO_ERROR_AGAIN,
  G_IO_ERROR_INVAL,
  G_IO_ERROR_UNKNOWN
} GIOError;
typedef enum
{
  G_SEEK_CUR,
  G_SEEK_SET,
  G_SEEK_END
} GSeekType;
typedef enum
{
  **G_IO_IN       GLIB_SYSDEF_POLLIN,**
  G_IO_OUT      GLIB_SYSDEF_POLLOUT,
  G_IO_PRI      GLIB_SYSDEF_POLLPRI,
  G_IO_ERR      GLIB_SYSDEF_POLLERR,
  G_IO_HUP      GLIB_SYSDEF_POLLHUP,
  G_IO_NVAL     GLIB_SYSDEF_POLLNVAL
} GIOCondition;

struct _GIOChannel
{
  guint channel_flags;

```
   Can anyone help me

---

