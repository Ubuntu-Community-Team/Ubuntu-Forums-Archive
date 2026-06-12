---
title: "error compiling gtk+-1.2.0"
date: 2009-10-27
forum: General Help
---

### Post by bluelightav on 2009-10-27
Hi,
I am getting this error compiling gtk+-1.2.0 . Does anybody know what I have to do here? I checked on the web but no success.

root@jaunty32bit:/home/blue/Desktop/gtk+-1.2.0# make
make  all-recursive
make[1]: Entering directory `/home/blue/Desktop/gtk+-1.2.0'
Making all in po
make[2]: Entering directory `/home/blue/Desktop/gtk+-1.2.0/po'
make[2]: Leaving directory `/home/blue/Desktop/gtk+-1.2.0/po'
Making all in gdk
make[2]: Entering directory `/home/blue/Desktop/gtk+-1.2.0/gdk'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"Gdk\"		-I..			-DGTK_NO_CHECK_CASTS 		-DUSE_XIM					-I/usr/include/glib-1.2 -I/usr/lib/glib/include -D_REENTRANT			     -g -O2 -Wall -c gdkwindow.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"Gdk\" -I.. -DGTK_NO_CHECK_CASTS -DUSE_XIM -I/usr/include/glib-1.2 -I/usr/lib/glib/include -D_REENTRANT -g -O2 -Wall -c -fPIC -DPIC gdkwindow.c -o gdkwindow.lo
gdkwindow.c: In function 'gdk_window_set_role':
gdkwindow.c:1199: warning: pointer targets in passing argument 7 of 'XChangeProperty' differ in signedness
gdkwindow.c: In function 'gdk_window_shape_combine_mask':
gdkwindow.c:1893: warning: unused variable 'pixmap'
gdkwindow.c:1892: warning: unused variable 'window_private'
gdkwindow.c: In function 'gdk_add_rectangles':
gdkwindow.c:2365: warning: implicit declaration of function 'XShapeGetRectangles'
gdkwindow.c:2365: error: 'ShapeBounding' undeclared (first use in this function)
gdkwindow.c:2365: error: (Each undeclared identifier is reported only once
gdkwindow.c:2365: error: for each function it appears in.)
gdkwindow.c:2365: warning: assignment makes pointer from integer without a cast
gdkwindow.c: In function 'gdk_propagate_shapes':
gdkwindow.c:2502: warning: implicit declaration of function 'XShapeCombineRectangles'
gdkwindow.c:2502: error: 'ShapeBounding' undeclared (first use in this function)
gdkwindow.c:2503: error: 'ShapeSet' undeclared (first use in this function)
gdkwindow.c: In function 'gdk_window_set_child_shapes':
gdkwindow.c:2525: warning: unused variable 'private'
gdkwindow.c: In function 'gdk_window_merge_child_shapes':
gdkwindow.c:2542: warning: unused variable 'private'
make[2]: *** [gdkwindow.lo] Error 1
make[2]: Leaving directory `/home/blue/Desktop/gtk+-1.2.0/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/blue/Desktop/gtk+-1.2.0'
make: *** [all-recursive-am] Error 2
root@jaunty32bit:/home/blue/Desktop/gtk+-1.2.0#

---

### Post by Giblet5 on 2009-10-27
Attack only the first Error.

That would be
gdkwindow.c:2365: error: 'ShapeBounding' undeclared (first use in this function)

So, go to line 2365 of gdkwindow.c and find out why the symbol ShapeBounding is not declared. ```
vi +2365 gdkwindow.c
```

Odds are, this is defined in a header during the configure process and you forgot to run configure first. That's just a guess.

---

### Post by bluelightav on 2009-10-27
Hi, thx for the help. I ran ./configure without any error. Here some lines from gdkwindow.c

static void
gdk_add_rectangles (Display           *disp,
		    Window             win,
		    struct _gdk_span **spans,
		    gint               basew,
		    gint               baseh,
		    gint               x,
		    gint               y)
{
  gint a, k;
  gint x1, y1, x2, y2;
  gint rn, ord;
  XRectangle *rl;
  
  rl = XShapeGetRectangles (disp, win, ShapeBounding, &rn, &ord);
  if (rl)
    {
      /* go through all clip rects in this window's shape */
      for (k = 0; k < rn; k++)
	{
	  /* for each clip rect, add it to each line's spans */
	  x1 = x + rl[k].x;
	  x2 = x + rl[k].x + (rl[k].width - 1);
	  y1 = y + rl[k].y;
	  y2 = y + rl[k].y + (rl[k].height - 1);
	  if (x1 < 0)
	    x1 = 0;
	  if (y1 < 0)
	    y1 = 0;
	  if (x2 >= basew)
	    x2 = basew - 1;
	  if (y2 >= baseh)
	    y2 = baseh - 1;
	  for (a = y1; a <= y2; a++)
	    {
	      if ((x2 - x1) >= 0)
		gdk_add_to_span (&spans[a], x1, x2);
	    }
	}
      XFree (rl);
    }
}

---

