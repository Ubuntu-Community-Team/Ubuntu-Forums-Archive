---
title: "Handling .bin/.cue"
date: 2009-09-03
forum: General Help
---

### Post by desperateone on 2009-09-03
I run bchunk on a .bin/.cue pair and I get this:
```
@ls
-rw-r--r-- 1 me me 8.8M 2009-09-03 21:22 stuff01.cdr
-rw-r--r-- 1 me me  21M 2009-09-03 21:22 stuff02.iso
-rw-r--r-- 1 me me  18M 2009-09-03 21:22 stuff03.cdr
-rw-r--r-- 1 me me  11M 2009-09-03 21:22 stuff04.cdr
-rw-r--r-- 1 me me  17M 2009-09-03 21:22 stuff05.cdr
-rw-r--r-- 1 me me  15M 2009-09-03 21:23 stuff06.cdr
-rw-r--r-- 1 me me  11M 2009-09-03 21:23 stuff07.cdr
-rw-r--r-- 1 me me  31M 2009-09-03 21:23 stuff08.cdr
-rw-r--r-- 1 me me  18M 2009-09-03 21:23 stuff09.cdr
-rw-r--r-- 1 me me  28M 2009-09-03 21:23 stuff10.cdr
-rw-r--r-- 1 me me  18M 2009-09-03 21:23 stuff11.cdr
-rw-r--r-- 1 me me  26M 2009-09-03 21:23 stuff12.cdr
-rw-r--r-- 1 me me  25M 2009-09-03 21:23 stuff13.cdr
-rw-r--r-- 1 me me  37M 2009-09-03 21:23 stuff14.cdr
-rw-r--r-- 1 me me  25M 2009-09-03 21:23 stuff15.cdr
-rw-r--r-- 1 me me  33M 2009-09-03 21:23 stuff16.cdr
-rw-r--r-- 1 me me  16M 2009-09-03 21:23 stuff17.cdr
-rw-r--r-- 1 me me  18M 2009-09-03 21:23 stuff18.cdr
-rw-r--r-- 1 me me  21M 2009-09-03 21:23 stuff19.cdr
-rw-r--r-- 1 me me  41M 2009-09-03 21:23 stuff20.cdr
-rw-r--r-- 1 me me  44M 2009-09-03 21:23 stuff21.cdr
-rw-r--r-- 1 me me  20M 2009-09-03 21:23 stuff22.iso

```

Then I try to mount the .iso;

```
@sudo mount -o loop -t iso9660 stuff22.iso /media/things
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
And the other .iso too. Anyone know what's going on? Alternatively, anyone knows how to handle .mdf/.mds files?

---

