---
title: "compiling vlc"
date: 2009-11-10
forum: General Help
---

### Post by sandyd on 2009-11-10
When compiling VLC from git, i get a missing xkb-shm error.

any help?

---

### Post by mc4man on 2009-11-10
Are you sure it's not more like xcb-shm

search xcb in synaptic, you'll find the needed xcb libs and -devs there
(may be more than just libxcb-shm0-dev, maybe keep synaptic open for a bit

should be 5 in total - from last git log

> pkg_cv_XCB_CFLAGS=' '
pkg_cv_XCB_KEYSYMS_CFLAGS=' '
pkg_cv_XCB_KEYSYMS_LIBS='-lxcb-keysyms -lxcb  '
pkg_cv_XCB_LIBS='-lxcb  '
pkg_cv_XCB_RANDR_CFLAGS=' '
pkg_cv_XCB_RANDR_LIBS='-lxcb-randr -lxcb  '
pkg_cv_XCB_SHM_CFLAGS=' '
pkg_cv_XCB_SHM_LIBS='-lxcb-shm -lxcb  '
pkg_cv_XCB_XV_CFLAGS=' '
pkg_cv_XCB_XV_LIBS='-lxcb-xv -lxcb-shm -lxcb  '

---

### Post by sandyd on 2009-11-11
> **mc4man said:**
> Are you sure it's not more like xcb-shm

search xcb in synaptic, you'll find the needed xcb libs and -devs there
(may be more than just libxcb-shm0-dev, maybe keep synaptic open for a bit

should be 5 in total - from last git log
yeah, i meant xcb (typo)
yep. that was it.
thanks!

---

