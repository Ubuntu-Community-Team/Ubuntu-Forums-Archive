---
title: "problem with ghostscript jpeg =&gt; eps conversion"
date: 2010-02-19
forum: General Help
---

### Post by missfroguk on 2010-02-19
Hi all,

I'm trying to convert a jpg to eps with ghostscript using the command 
```
gs -sDEVICE=jpeg -dJPEGQ=100 -dNOPAUSE -dBATCH -dSAFER -r300 -sOutputFile=file1.jpg file1.eps
```

but I'm getting the error message

```
Error: /undefinedfilename in (file1.eps)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1155/1684(ro)(G)--   --dict:0/20(G)--   --dict:70/200(L)--
Current allocation mode is local
Last OS error: 2

```

Could anybody tell me what I'm doing wrong?

Thank you

---

### Post by kaibob on 2010-02-19
> **missfroguk said:**
> Hi all,

I'm trying to convert a jpg to eps with ghostscript using the command 
```
gs -sDEVICE=jpeg -dJPEGQ=100 -dNOPAUSE -dBATCH -dSAFER -r300 -sOutputFile=file1.jpg file1.eps
```
<snip>

Are you trying to convert JPEG to EPS or EPS to JPEG. You indicate the former, but your command appears to do the latter. If you do actually want to convert JPEG to EPS, you probably should be using Imagemagick or similar.

---

