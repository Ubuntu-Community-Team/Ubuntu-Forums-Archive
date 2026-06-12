---
title: "gscan2pdf:"
date: 2011-05-05
forum: General Help
---

### Post by astrobob.tk on 2011-05-05
Hey there,

I've been recently using gscan2pdf & everything was going fine until last week when i scanned about 47 pages, saved them in .Tiff & was post processing in "Scan Tailor". When scanning i forgot to crop the outside of the documents (the black parts) particularly the top/bottom parts. Anyways that's not the issue; the issue is that i was trying to import the 47 page .Tiff file into gscan2pdf & after numerous attempts, the import always resulted in the same result, which is now pages or thumbnails are shown.

In attempt to know what's going on, i started gscan2pdf from the terminal & here is the result of the import:

```
$ gscan2pdf
gscan2pdf 0.9.29
CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed at /usr/bin/gscan2pdf line 10353.
TIFFOpen: /home/*************
Warning: Failed to load TIFF image at /usr/bin/gscan2pdf line 1509.

*** unhandled exception in callback:
***   Failed to load image  '/home/username/tmp_custom/NyPBGboTR0/khHE_AtNEQ.tif': Failed to open  TIFF image at /usr/bin/gscan2pdf line 1497.
***  ignoring at /usr/share/perl5/Gtk2/Ex/Simple/List.pm line 164.
TIFFOpen: /home/************************************: Cannot open.
Warning: Failed to load TIFF image at /usr/bin/gscan2pdf line 1509.

```can anyone help with this problem ?

P.S.: I autoremoved gscan2pdf & installed it again but the problem persists, even with 1 page .tff's

---

### Post by astrobob.tk on 2011-05-06
bump

---

