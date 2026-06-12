---
title: "Archive Manager: .7z &amp; .rar not supported"
date: 2011-01-02
forum: General Help
---

### Post by astrobob.tk on 2011-01-02
Hello,

On my OS, Archive Manager doesn't recognize .7z & .rar as supported types, though the Ubuntu Help states that it supports .rar !!!

Here's what I get when I try to open such extensions:

> Could not create the archive

Archive type not supported.

How come is that happening ?

---

### Post by Vaphell on 2011-01-02
install:
- unrar
- p7zip-full

```
sudo apt-get install unrar p7zip-full
```

File-roller supports the following formats:
 * Tar (.tar) archives, including those compressed with
   gzip (.tar.gz, .tgz), bzip (.tar.bz, .tbz), bzip2 (.tar.bz2, .tbz2),
   compress (.tar.Z, .taz), lzip (.tar.lz, .tlz), lzop (.tar.lzo, .tzo),
   lzma (.tar.lzma) and xz (.tar.xz)
 * Zip archives (.zip)
 * Jar archives (.jar, .ear, .war)
 * 7z archives (.7z)
 * iso9660 CD images (.iso)
 * Lha archives (.lzh)
 * Single files compressed with gzip (.gz), bzip (.bz), bzip2 (.bz2),
   compress (.Z), lzip (.lz), lzop (.lzo), lzma (.lzma) and xz (.xz)

[b]File-roller doesn't perform archive operations by itself, but relies on
standard tools for this.[/b]

---

### Post by astrobob.tk on 2011-01-02
> **Vaphell said:**
> install:
- unrar
- p7zip-full

```
sudo apt-get install unrar p7zip-full
```File-roller supports the following formats:
 * Tar (.tar) archives, including those compressed with
   gzip (.tar.gz, .tgz), bzip (.tar.bz, .tbz), bzip2 (.tar.bz2, .tbz2),
   compress (.tar.Z, .taz), lzip (.tar.lz, .tlz), lzop (.tar.lzo, .tzo),
   lzma (.tar.lzma) and xz (.tar.xz)
 * Zip archives (.zip)
 * Jar archives (.jar, .ear, .war)
 * 7z archives (.7z)
 * iso9660 CD images (.iso)
 * Lha archives (.lzh)
 * Single files compressed with gzip (.gz), bzip (.bz), bzip2 (.bz2),
   compress (.Z), lzip (.lz), lzop (.lzo), lzma (.lzma) and xz (.xz)

[B]File-roller doesn't perform archive operations by itself, but relies on
standard tools for this.[/B]

thanks man, that worked. charming :D

---

### Post by frillip on 2011-07-22
Sorry to dig up an old thread, but I'd also like to add my thanks. I almost swallowed my own tongue when it came up with that error message!

---

