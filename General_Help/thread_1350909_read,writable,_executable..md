---
title: "read,writable, executable."
date: 2009-12-09
forum: General Help
---

### Post by Hunter2379 on 2009-12-09
Is there a way to make my linux scripts so that no one can read or write them except me, but that everyone can still execute them?

---

### Post by fluffman86 on 2009-12-09
chmod 711 filename

more info: [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

not sure exactly how well that will work though.  they may still need to have read permissions.  To read/execute, but not write:

chmod 755 filename

---

### Post by bodhi.zazen on 2009-12-09
You need to read it to execute it, lol

chmod 755

---

