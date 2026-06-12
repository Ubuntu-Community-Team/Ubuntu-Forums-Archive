---
title: "Fix filenames character encoding?"
date: 2010-03-23
forum: General Help
---

### Post by StuartN on 2010-03-23
I have a lot of files on a share that were saved from an Ubuntu, with the drive mounted with default Cifs mount options. All the filenames with foreign characters are messed up, for instance:

```
Touré -> Tour&#9500;&#8976;
```

The filenames look correct on the original machine that saved them, but not on the Nas they were saved to, or Ubuntu configured to mount with utf-8 nor on a Mac.

I tried ls | iconf -f iso-8859-1 -t utf-8, but the listing was still garbled, and the same with cp850 and a few other obvious suspects - the default encoding of a Cifs mount ("the nls_default specified during the local client kernel build") appears to be something else. What encoding is used by a default Ubuntu installation if none is specified in the mount command?

Mounting the share with the Cifs option "iocharset=utf8" would obviously have prevented the problem in the first place, but how do I fix up the existing filenames?

---

