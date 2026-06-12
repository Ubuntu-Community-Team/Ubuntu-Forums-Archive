---
title: "Convert Firefox cache hex dump to plain text"
date: 2012-03-11
forum: General Help
---

### Post by Dingbats on 2012-03-11
I've got some Firefox cache that I want to parse and read.  It's stored gzipped, and when viewed through about:cache, it gives you a hex dump of the format:

```
00000000:  1f  8b  08  00  00  00  00  00  00  03  ac  57  6d  53  db  38  ...........WmS.8
```

etc. for many lines.  I want to convert this to a binary file and then uncompress it to plain text.  I tried saving it to a text file and running xxd -r on it, but that produces an abnormally small file of only a handful of bytes, so something must be wrong.

How do I convert this dump to plain text?

---

### Post by Dingbats on 2012-03-13
Anyone?  Any hex wizards?

---

### Post by adit on 2012-04-10
The builtin cache viewer in firefox (about:cache) is not good.  I use the firefox addon "CacheViewer Continued" for that purpose

---

