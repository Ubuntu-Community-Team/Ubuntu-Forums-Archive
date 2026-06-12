---
title: "(gedit:9912): GdkPixbuf-CRITICAL in terminal"
date: 2010-12-07
forum: General Help
---

### Post by iosuna86 on 2010-12-07
Whenever I execute the command "sudo gedit /etc/apt/sources.list" a bunch of lines fill the terminal screen, all of them starting with (gedit:9912): GdkPixbuf-CRITICAL. Here are some of them: 

> (gedit:9912): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:9912): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:9912): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:9912): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:9912): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failedThe thing is that gedit opens and that I can manage to do what I want with the file. But this has never happened to me before. Nothing seems to have stopped working, but still, there might be something wrong. 

I did a fresh install of Maverick Meerkat 2 days ago and this started yesterday. 

I haven't found any threads and I have googled it and found nothing. 

Thanks in advance!

---

### Post by iosuna86 on 2010-12-08
Anyone?

I am having the same problem over and over. 

The number of "(gedit:*)" does change, though. Now I see the following:
> 
(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gedit:5127): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

Is it so uncommon? I haven't seen anything related.

---

### Post by iosuna86 on 2010-12-14
I did a clean install and I still have that problem.

It doesn't prevent me from doing anything, but still, it is quite annoying.

---

### Post by iosuna86 on 2010-12-20
I figured it out.

I was a problem of the theme. I installed elementary theme with some extras, now I went back to the default theme and get no error messages while using the terminal.

---

### Post by nhianho on 2011-01-12
Boom !

I got the same problem after trying out a new theme.

Any suggestion about how to fix it?

---

### Post by oraerk on 2011-01-13
use correct theme / submit bug to elementary maintainer

---

