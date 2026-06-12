---
title: "how to get cpp back from lib  .so file?"
date: 2011-03-23
forum: General Help
---

### Post by andrissh on 2011-03-23
Hi guys, 
I accidentally deleted a .cpp file with some valuable code of mine.
It was part of my own library: libandrissh.so
How can I recover it? I tried scalpel, but did not find it.
I was wondering if I could somehow extract the info from my .so or other files that are in my library. I think this could be possible, because my programs using the library still work.

any suggestions?

---

### Post by sedawk on 2011-03-23
Normally editors do some backups themselves, so check
if your editor created a backup file that is still
available. E.g. list all files starting with a dot in
the source directory, or in /var/tmp, or ...
(depends on your editor, so read the doc)

If you have compiled with "-g" and the "debug symbols" are
still in the library there might be a change to
recover your code by using a so called "decompiler" for c++.
(Never used one myself, check the web!).
Otherwise the data you can recover might only be what
is more or less the data in your header file.

---

