---
title: "digitemp on amd64"
date: 2010-05-11
forum: General Help
---

### Post by Vanadaar on 2010-05-11
Anyone out there using digitemp on amd64 that has it reading from a DS9490R? It works fine from 32 bit.

---

### Post by berland on 2010-05-30
I seem to have the same problem with Ubuntu 10.04 and digitemp_DS2490. It works on a 32-bit machine (asus eee pc 1005he) but does not work on two 64-bit machines (same motherboard, Asus M3N78-EM)

---

### Post by mike4ubuntu on 2010-08-09
how did you get it to work on 32bit Lucid?  It was working in Karmic for me, but now it seems to be broken again in Lucid

```

$ sudo modprobe -r ds2490
$ sudo digitemp_DS2490 -q -a -o "%F" -i
Found DS2490 device #1 at 001/005

```

but that's it.  It won't display the temperature anymore.

---

