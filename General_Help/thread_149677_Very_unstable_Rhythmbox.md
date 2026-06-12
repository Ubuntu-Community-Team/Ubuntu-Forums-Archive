---
title: "Very unstable Rhythmbox"
date: 2006-03-24
forum: General Help
---

### Post by mikaPELL on 2006-03-24
Hi, I have a problem with Rhythmbox. I have a folder on my computer with all of my music ( /home/mikapell/knato/mp3 ) and therefore would like to use the function "Check folder for updates" in the later Rhythmbox versions.
This means that I don't want to use the 0.9.1 version in the repositories.
On the MighMos site I found a .deb of the 0.9.3.1 version that worked with no hassle on my laptop. On my stationary computer however, it crashes every two or three windows, with no warning or anything.
If i run "rhythmbox -d" to debug, I get this (eventually, all of the output would be too much to quote)
```
SWFDEC: ERROR: swfdec_shape.c(374): swf_shape_add_styles: unknown fill style type 0x02
SWFDEC: ERROR: swfdec_shape.c(374): swf_shape_add_styles: unknown fill style type 0x02
SWFDEC: ERROR: swfdec_shape.c(374): swf_shape_add_styles: unknown fill style type 0x03
SWFDEC: ERROR: swfdec_shape.c(374): swf_shape_add_styles: unknown fill style type 0x1a
SWFDEC: ERROR: swfdec_shape.c(374): swf_shape_add_styles: unknown fill style type 0x14
SWFDEC: ERROR: swfdec_shape.c(374): swf_shape_add_styles: unknown fill style type 0x6f
[0x82c19b8] [rb_metadata_gst_fakesink_handoff_cb] rb-metadata-gst.c:527 (18:13:57): in fakesink handoff
[0x82c19b8] [rb_metadata_load] rb-metadata-gst.c:887 (18:13:57): duration query succeeded
Minnesegmentsfeil

```
"Minnesegmentsfeil" is Norwegian and means something like "memory segment fault". I've tried reinstalling, deleting the library xml (and now rb doesn't even find all of my songs) and whatever I could think of. 
Please help me if you can - Mikael :)

---

### Post by trent dillman on 2006-03-24
looks like a problem with an swf plugin to me, but i'm not sure how to fix it...

---

### Post by mikaPELL on 2006-03-24
That might be the case, I struggled quite a lot to get flash working. 
Any other suggestions to how I might fix this?

---

### Post by trent dillman on 2006-03-24
I don't think the proprietary plugin outputs anything, so it's probably in with your video plugins.

---

### Post by mikaPELL on 2006-03-24
I don't know WHY, but when I did a "sudo apt-get remove swf-*", the problem seemingly went away... Thanks for helping :)

---

