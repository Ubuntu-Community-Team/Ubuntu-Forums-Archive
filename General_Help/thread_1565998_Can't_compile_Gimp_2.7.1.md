---
title: "Can't compile Gimp 2.7.1"
date: 2010-09-01
forum: General Help
---

### Post by Ancanus on 2010-09-01
Hey guys, wondering if you could help me out with this.

I've installed *babl* and *gegl* and I've already successfully ran **./configure** for Gimp 2.7.1

However, when attempting to **make**, I get this:

```

...
  CC     gimpcolorbutton.lo
  CC     gimpcolordisplay.lo
  CC     gimpcolordisplaystack.lo
  CC     gimpcolorhexentry.lo
  CC     gimpcolornotebook.lo
gimpcolornotebook.c:64: error: expected declaration specifiers or ‘...’ before ‘GtkNotebookPage’
gimpcolornotebook.c:311: error: expected declaration specifiers or ‘...’ before ‘GtkNotebookPage’
make[2]: *** [gimpcolornotebook.lo] Error 1
make[2]: Leaving directory `/home/ancanus/Programs/gimp-2.7.1/libgimpwidgets'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ancanus/Programs/gimp-2.7.1'
make: *** [all] Error 2

```I got the tar from [ftp://ftp.gimp.org/pub/gimp/v2.7/](ftp://ftp.gimp.org/pub/gimp/v2.7/). Is this an error on the source code, or a misconfiguration on my side? How may I proceed?

Thank you guys, you are the best!

---

### Post by tkluck on 2010-09-09
I found your post when stumbling on the same problem. Here's how to fix it.

The problem is in this piece of code in gtk/gtknotebook.h (not part of the Gimp)

```
#if !defined (GTK_DISABLE_DEPRECATED) || defined (GTK_COMPILATION)
typedef struct _GtkNotebookPage   GtkNotebookPage;
#endif
```

So it seems that Gimp defines GTK_DISABLE_DEPRECATED. I worked around it by setting the GTK_COMPILATION flag:

CFLAG="-DGTK_COMPILATION" ./configure

This seems to work for now; I'm still compiling so I don't know about any bad side-effects.

---

### Post by Ancanus on 2010-09-30
> **tkluck said:**
> I found your post when stumbling on the same problem. Here's how to fix it.

The problem is in this piece of code in gtk/gtknotebook.h (not part of the Gimp)

```
#if !defined (GTK_DISABLE_DEPRECATED) || defined (GTK_COMPILATION)
typedef struct _GtkNotebookPage   GtkNotebookPage;
#endif
```So it seems that Gimp defines GTK_DISABLE_DEPRECATED. I worked around it by setting the GTK_COMPILATION flag:

CFLAG="-DGTK_COMPILATION" ./configure

This seems to work for now; I'm still compiling so I don't know about any bad side-effects.

Thanks! This fixed it for me.

---

