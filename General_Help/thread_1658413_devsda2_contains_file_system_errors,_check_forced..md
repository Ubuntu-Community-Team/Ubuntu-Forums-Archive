---
title: "/dev/sda2 contains file system errors, check forced."
date: 2011-01-02
forum: General Help
---

### Post by D4Y.V on 2011-01-02
Recently installed Ubuntu 10.10
So, I apparently have filesystem errors, so I booted the computer into recovery mode.
```
/dev/sda2: Entry 'Cookies-journal' in /home/jiko/.config/chromium/Default (3080505) has incorrect filetype (was 1, should be 7)


/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
mountall: fsck / [342] terminated with status 4

mountall: Filesystem has errors: /
Errors were found while checking the disk drive for /
Press f to attempt to fix errors, I to ignore, S to skip to mounting or M for manual recovery
_
```
I have no clue where to go from here. Any help would be appreciated.

---

### Post by TeoBigusGeekus on 2011-01-02
Boot up with a live cd, open terminal and give
```
sudo fsck /dev/sda2
```

---

