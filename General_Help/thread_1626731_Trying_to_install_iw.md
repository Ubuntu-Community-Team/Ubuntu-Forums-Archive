---
title: "Trying to install iw"
date: 2010-11-20
forum: General Help
---

### Post by pandaxcore on 2010-11-20
so im trying to install iw so i can get my 3945 abg card to inject properly

im coming up with this error

[HTML]cody@WARMACHINE:~$ cd iw-0.9.1*
cody@WARMACHINE:~/iw-0.9.1$ make
 CC   mpath.o
mpath.c: In function ‘print_mpath_handler’:
mpath.c:39: error: ‘NL80211_MPATH_INFO_DSN’ undeclared (first use in this function)
mpath.c:39: error: (Each undeclared identifier is reported only once
mpath.c:39: error: for each function it appears in.)
mpath.c:39: error: array index in initializer not of integer type
mpath.c:39: error: (near initialization for ‘mpath_policy’)
make: *** [mpath.o] Error 1
cody@WARMACHINE:~/iw-0.9.1$ 
[/HTML]

any idea whats goin on?

---

### Post by gordintoronto on 2010-11-20
Why not use Synaptic Package Manager to install it? I think it even has the latest version.

---

### Post by pandaxcore on 2010-11-20
> **gordintoronto said:**
> Why not use Synaptic Package Manager to install it? I think it even has the latest version.

if this is true i will feel like a sizeable douchebag

---

