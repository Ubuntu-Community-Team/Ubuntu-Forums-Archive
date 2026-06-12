---
title: "evince compile problem"
date: 2011-03-20
forum: General Help
---

### Post by parag14 on 2011-03-20
hi..
when i compile evince from its source code, i am able to run ./configure properly, but when i run make the following output is displayed.

```
make  all-recursive
make[1]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0'
Making all in cut-n-paste
make[2]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste'
Making all in zoom-control
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/zoom-control'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/zoom-control'
Making all in toolbar-editor
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/toolbar-editor'
make  all-am
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/toolbar-editor'
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/toolbar-editor'
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/toolbar-editor'
Making all in totem-screensaver
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/totem-screensaver'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/totem-screensaver'
Making all in smclient
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/smclient'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/smclient'
Making all in gimpcellrenderertoggle
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/gimpcellrenderertoggle'
  GEN    gimpwidgetsmarshal.h
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/gimpcellrenderertoggle'
Making all in synctex
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/synctex'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste/synctex'
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste'
make[2]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/cut-n-paste'
Making all in data
make[2]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data'
Making all in icons
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons'
Making all in 16x16
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16'
Making all in actions
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16/actions'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16/actions'
Making all in apps
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16/apps'
Making all in mimetypes
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16/mimetypes'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16/mimetypes'
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16'
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/16x16'
Making all in 22x22
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22'
Making all in actions
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22/actions'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22/actions'
Making all in apps
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22/apps'
Making all in mimetypes
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22/mimetypes'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22/mimetypes'
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22'
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/22x22'
Making all in 24x24
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24'
Making all in actions
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24/actions'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24/actions'
Making all in apps
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24/apps'
Making all in mimetypes
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24/mimetypes'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24/mimetypes'
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24'
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/24x24'
Making all in 32x32
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32'
Making all in actions
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32/actions'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32/actions'
Making all in mimetypes
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32/mimetypes'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32/mimetypes'
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32'
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48'
Making all in actions
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48/actions'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48/actions'
Making all in apps
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48/apps'
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48'
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/48x48'
Making all in scalable
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable'
Making all in actions
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable/actions'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable/actions'
Making all in apps
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable/apps'
Making all in mimetypes
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable/mimetypes'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable/mimetypes'
make[5]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable'
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons/scalable'
make[4]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons'
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data/icons'
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/data'
LC_ALL=C /usr/bin/intltool-merge -d -u -c ../po/.intltool-merge-cache ../po evince.desktop.in evince.desktop
Found cached translation database
Merging translations into evince.desktop.
  GEN    org.gnome.evince.Daemon.service
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data'
make[2]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/data'
Making all in libdocument
make[2]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/libdocument'
  GEN    stamp-ev-document-type-builtins.c
  GEN    stamp-ev-document-type-builtins.h
make  all-am
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/libdocument'
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/libdocument'
make[2]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/libdocument'
Making all in backend
make[2]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/backend'
Making all in pdf
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/backend/pdf'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/backend/pdf'
Making all in comics
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/backend/comics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/backend/comics'
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/backend'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/backend'
make[2]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/backend'
Making all in libview
make[2]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/libview'
make  all-am
make[3]: Entering directory `/media/New_Volume/untitled folder/evince-2.32.0/libview'
  CC     libevview_la-ev-document-model.lo
  CC     libevview_la-ev-jobs.lo
  CC     libevview_la-ev-job-scheduler.lo
  CC     libevview_la-ev-page-cache.lo
  CC     libevview_la-ev-pixbuf-cache.lo
  CC     libevview_la-ev-print-operation.lo
  CC     libevview_la-ev-transition-animation.lo
  CC     libevview_la-ev-view.lo
  CC     libevview_la-ev-view-accessible.lo
  CC     libevview_la-ev-view-presentation.lo
  CC     libevview_la-ev-view-type-builtins.lo
  CCLD   libevview.la
make[3]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/libview'
make[2]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0/libview'
make[1]: Leaving directory `/media/New_Volume/untitled folder/evince-2.32.0'
ev-view.c: In function ‘compute_scroll_increment’:
ev-view.c:841: warning: passing argument 1 of ‘cairo_region_create_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2603: note: expected ‘const struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c:849: warning: passing argument 3 of ‘cairo_region_get_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2632: note: expected ‘struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c:866: warning: passing argument 3 of ‘cairo_region_get_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2632: note: expected ‘struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c: In function ‘ev_view_form_field_get_region’:
ev-view.c:1946: warning: passing argument 1 of ‘cairo_region_create_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2603: note: expected ‘const struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c: In function ‘ev_view_create_annotation’:
ev-view.c:2858: warning: passing argument 1 of ‘cairo_region_create_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2603: note: expected ‘const struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c: In function ‘merge_selection_region’:
ev-view.c:5896: warning: passing argument 3 of ‘cairo_region_get_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2632: note: expected ‘struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c:5899: warning: passing argument 2 of ‘cairo_region_union_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2667: note: expected ‘const struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c:5901: warning: passing argument 3 of ‘cairo_region_get_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2632: note: expected ‘struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
ev-view.c:5904: warning: passing argument 2 of ‘cairo_region_union_rectangle’ from incompatible pointer type
/usr/include/cairo/cairo.h:2667: note: expected ‘const struct cairo_rectangle_int_t *’ but argument is of type ‘struct GdkRectangle *’
/bin/sed: can't read folder/evince-2.32.0/libdocument/libevdocument.la: No such file or directory
libtool: link: `folder/evince-2.32.0/libdocument/libevdocument.la' is not a valid libtool archive
make[3]: *** [libevview.la] Error 1
make[2]: *** [all] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

```

i am not able to ascertain the source of this error, even though i seem to have the file in question-libevdocument.la
what do i do now to remove this error?

---

