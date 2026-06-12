---
title: "Input/output error on Rhythmbox database"
date: 2010-07-14
forum: General Help
---

### Post by jackhynes on 2010-07-14
Rhythmbox is segfaulting when I open it:
```
$ rhythmbox

(rhythmbox:15550): Rhythmbox-WARNING **: could not import python module 'rb'
ImportError: No module named rb
I/O error : Input/output error
I/O error : Input/output error
I/O warning : failed to load external entity "~/.local/share/rhythmbox/rhythmdb.xml"
Segmentation fault (core dumped)

```

So I tried opening the database file and get:
```
 $ gedit '~/.local/share/rhythmbox/rhythmdb.xml' 

** (gedit:13971): WARNING **: Hit unhandled case 0 (Error opening file: Input/output error) in parse_error.

```

Is there any way to recover the database?

---

