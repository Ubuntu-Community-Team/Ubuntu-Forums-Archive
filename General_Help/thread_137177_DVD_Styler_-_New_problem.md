---
title: "DVD Styler - New problem"
date: 2006-02-27
forum: General Help
---

### Post by Haegin on 2006-02-27
Hi,
I have been trying to install dvdstyler on my pc and I have used the repo for breezy provided on their website but when I run dvdstyler I just get the following:
```

harry@geswick:~$ dvdstyler
Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 102,wx containers,compatible with 2.4),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

```
As far as I know this is a new error and I haven't a clue how to fix it. Do I need to compile from source?

---

### Post by Haegin on 2006-04-01
Ok, I found it was to do with an odd wxWidgets library

---

