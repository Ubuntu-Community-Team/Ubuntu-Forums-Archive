---
title: "Ghostscript crashes with unreoverable error"
date: 2011-07-15
forum: General Help
---

### Post by joefremont on 2011-07-15
We are having trouble converting some PDF files to images using GhostScript.  The PDF files are produced by some clients in Japan, I have tried everything I can think of to get gs to convert it but so far no luck.  I have tried this on both 10.04 server and 11.04 server.

The command line I am using is:

```
 /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=ppmraw -dPDFFitPage -r300x300 -sOutputFile=p%04d.ppm Birt.pdf
```

The result I get is:

```
Error: /undefined in findresource
Operand stack:
   --dict:6/15(L)--   F2   12   --dict:5/5(L)--   --dict:5/5(L)--   HeiseiKakuGo-W5-UniJIS-UCS2-H   --dict:10/12(ro)(G)--   --nostringval--   CIDFontObject   --dict:6/6(L)--   --dict:6/6(L)--   Adobe-Japan1
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1878   1   3   %oparray_pop   1877   1   3   %oparray_pop   1861   1   3   %oparray_pop   --nostringval--   --nostringval--   2   1   2   --nostringval--   %for_pos_int_continue   --nostringval--   --nostringval--   --nostringval--   --nostringval--   %array_continue   --nostringval--   false   1   %stopped_push   --nostringval--   %loop_continue   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   %array_continue   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   %loop_continue
Dictionary stack:
   --dict:1158/1684(ro)(G)--   --dict:1/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:108/127(ro)(G)--   --dict:288/300(ro)(G)--   --dict:22/25(L)--   --dict:6/8(L)--   --dict:21/40(L)--   --dict:1/1(ro)(G)--   --dict:1/1(ro)(G)--   --dict:6/15(L)--
Current allocation mode is local
Last OS error: 2
GPL Ghostscript 8.71: Unrecoverable error, exit code 1

```

Any suggestions that will help convert the files would be helpful.

---

### Post by joefremont on 2011-07-18
Bump!

---

### Post by joefremont on 2011-07-25
The sound of the crickets is deafening, does anyone have any idea?

---

