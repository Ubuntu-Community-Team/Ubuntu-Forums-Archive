---
title: "ps2pdf doesn't work"
date: 2009-07-03
forum: General Help
---

### Post by nmaster on 2009-07-03
I was converting a djvu to a pdf by first converting to a ps file.  Here's what happened.

```

neal@ubuntu:~/Desktop$ djvups *.djvu siss.ps
neal@ubuntu:~/Desktop$ ps2pdf siss.ps siss.pdf
Error: /rangecheck in --image--
Operand stack:
   --dict:8/8(L)--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1862   1   3   %oparray_pop   1861   1   3   %oparray_pop   1845   1   3   %oparray_pop   1739   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   1766   1   3   %oparray_pop
Dictionary stack:
   --dict:1151/1684(ro)(G)--   --dict:0/20(G)--   --dict:111/200(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 4853
GPL Ghostscript 8.64: Unrecoverable error, exit code 1

```
i tried removing ghostscript and then reinstalling it, but the same thing happens.  i know there are other ways to convert djvu files to pdfs; im not asking about that.  i want to fix ghostscript though.  doesn't anyone have a suggestion?


extra info: none of the ps2pdf* commands work.  they all give the same error.

---

### Post by blueridgedog on 2009-07-03
Have you tested it with a different file?  Just to isolate the error, I would test it with a native *.ps file first.

---

