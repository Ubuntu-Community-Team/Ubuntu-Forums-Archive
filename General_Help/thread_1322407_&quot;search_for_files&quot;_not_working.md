---
title: "&quot;search for files&quot; not working"
date: 2009-11-10
forum: General Help
---

### Post by gamelover25 on 2009-11-10
I'm having an problem with the &#8220;search for files&#8221; tool.  I'm running ubuntu 9.10, on dell xps m1530, and whenever I click on search from files (Accessories>search for files) and I type in a file name and click find, it immediately closes.  Does anyone know a fix for this?

EDIT: This is the log from the terminal

```
** (gnome-search-tool:2084): WARNING **: Invalid borders specified for theme pixmap:
        /home/jessy/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image

** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Could not load spinner rest icon


(gnome-search-tool:2084): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-search-tool:2084): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-search-tool:2084): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-search-tool:2084): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(gnome-search-tool:2084): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

** (gnome-search-tool:2084): CRITICAL **: select_spinner_image: assertion `details->current_image != NULL' failed
**
ERROR:gsearchtool-spinner.c:666:bump_spinner_frame_cb: assertion failed: (frame != NULL)
Aborted

```

---

### Post by blueridgedog on 2009-11-10
This happens no mater what you type as a search?  How about something simple such as putting in *.txt for all text files?  I have a clean 9.10 install and it work as expected.

---

### Post by mo.reina on 2009-11-10
you can use the find command from the terminal if you urgently need to find files before the problem is resolved.

```
find /. -name **FILENAME**
```

---

### Post by fluffman86 on 2009-11-10
Open applications > accessories > terminal and run
```
gnome-search-tool
```
Then run your search and let us know if you get any errors posted in the terminal.

---

### Post by gamelover25 on 2009-11-11
> **fluffman86 said:**
> Open applications > accessories > terminal and run
```
gnome-search-tool
```
Then run your search and let us know if you get any errors posted in the terminal.

This is what i get

```
** (gnome-search-tool:2084): WARNING **: Invalid borders specified for theme pixmap:
        /home/jessy/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image

** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:2084): WARNING **: Could not load spinner rest icon


(gnome-search-tool:2084): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-search-tool:2084): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-search-tool:2084): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-search-tool:2084): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(gnome-search-tool:2084): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

** (gnome-search-tool:2084): CRITICAL **: select_spinner_image: assertion `details->current_image != NULL' failed
**
ERROR:gsearchtool-spinner.c:666:bump_spinner_frame_cb: assertion failed: (frame != NULL)
Aborted

```

---

### Post by blueridgedog on 2009-11-11
Given the error, I would try a different theme (the default one), then test the search.

---

### Post by i.siddharth.iitd on 2010-07-09
I get the same error. I figured out the cause, but not the best solution.

The problem seems to be the Mac4Lin icon set. I bet you are using the same. The icon it displays while searching (the "searching" logo) is not available, I think. That's what it means by "Could not load spinner rest icon".

So just changing the icon set solves the problem, ofcourse. But I love Mac4Lin icon set, so I would definitely encourage a more appropriate solution so that Mac4Lin can still be used.

---

