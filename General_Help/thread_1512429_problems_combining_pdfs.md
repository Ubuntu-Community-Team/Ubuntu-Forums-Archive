---
title: "problems combining pdfs"
date: 2010-06-18
forum: General Help
---

### Post by craq on 2010-06-18
I want to join multiple pdfs into one document. There are lots of ways, but the first two I tried have problems:

PDFTK:
pdftk *.pdf cat output all_images.pdf
works fine from the terminal, but when called from matlab I get the following error:
```
pdftk: /home/username/software/m2010a/unix/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by pdftk)
```

even if I call the command indirectly via a bash script.

GHOSTSCRIPT:
gs -dNOPAUSE -sDEVICE=pdfwrite -sOUTPUTFILE=all_images.pdf -dBATCH *.pdf
works fine, until I try to use it recursively. That is, I want to add more pages to my initial 'all_images.pdf' file. Then I get 

```
GPL Ghostscript 8.71 (2010-02-10)
Copyright (C) 2010 Artifex Software, Inc.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
Processing pages 1 through 1.
Page 1
Loading NimbusSanL-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n019003l.pfb... 2556592 1214458 2101220 796997 3 done.
Loading Symbol font from /var/lib/defoma/gs.d/dirs/fonts/Symbol.pfb... 2596784 1267151 2161508 852632 3 done.
Processing pages 1 through 1.
Page 1
Processing pages 1 through 1.
Page 1
Processing pages 1 through 1.
Page 1
Processing pages 1 through 1.
Page 1
   **** Error: Cannot find a %%EOF marker anywhere in the file.
   **** Warning:  An error occurred while reading an XREF table.
   **** The file has been damaged.  This may have been caused
   **** by a problem while converting or transfering the file.
   **** Ghostscript will attempt to recover the data.
Error: /undefined in --run--
Operand stack:
   1   --dict:5/5(ro)(G)--   (\323\250\361\323r\232y_o7\215\322)
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1878   1   3   %oparray_pop   1877   1   3   %oparray_pop   1861   1   3   %oparray_pop   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   --nostringval--   %loop_continue   --nostringval--
Dictionary stack:
   --dict:1155/1684(ro)(G)--   --dict:1/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:108/127(ro)(G)--   --dict:288/300(ro)(G)--   --dict:20/25(L)--
Current allocation mode is local
GPL Ghostscript 8.71: Unrecoverable error, exit code 1
```

Does anybody know how to fix either of these errors?

---

### Post by StuartN on 2010-06-18
> **craq said:**
> works fine from the terminal, but when called from matlab I get the following error:

I suspect that your path as set in the terminal provides a route to the required library, but the path set within Matlab, and in a script, do not.

echo $PATH will show you your path, which you can then set or add to the PATH in a script, or set within Matlab.

---

