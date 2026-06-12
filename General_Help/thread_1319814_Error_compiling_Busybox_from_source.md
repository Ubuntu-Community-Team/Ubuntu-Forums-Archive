---
title: "Error compiling Busybox from source"
date: 2009-11-08
forum: General Help
---

### Post by LuisPT on 2009-11-08
Some help please guys.

I download busybox source directly from busybox site.

I do my config (make menuconfig) and when I do make allmost every busybox shell gives this error:

```
util-linux/mount.c:485: warning: format not a string literal and no format arguments
util-linux/mount.c: In function ‘find_kernel_nfs_mount_version’:
util-linux/mount.c:869: **[COLOR="Red"][B]warning: dereferencing type-punned pointer will break strict-aliasing rules**[/COLOR][/B]
util-linux/mount.c:872: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:877: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:881: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c: In function ‘get_mountport’:
util-linux/mount.c:901: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:902: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:919: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c: In function ‘nfsmount’:
util-linux/mount.c:1272: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1294: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1296: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1298: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1298: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1312: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1517: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c: In function ‘singlemount’:
util-linux/mount.c:1721: warning: format not a string literal and no format arguments
util-linux/mount.c:1743: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1744: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1745: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1749: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c: In function ‘mount_main’:
util-linux/mount.c:1851: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1865: warning: dereferencing type-punned pointer will break strict-aliasing rules
util-linux/mount.c:1936: warning: dereferencing type-punned pointer will break strict-aliasing rules

```

The make goes to the end and finish with no fatal error.

What's the problem with busybox compilation????

Thanks in advance.

---

