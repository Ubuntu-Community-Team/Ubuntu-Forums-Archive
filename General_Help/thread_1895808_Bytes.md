---
title: "Bytes"
date: 2011-12-15
forum: General Help
---

### Post by radu992 on 2011-12-15
How can I tr, let's say 7 bytes of zero into 7 bytes of 7 or 8 or whatever? I tried something like this : first I create a file with dd if=/dev/zero of=/myfile bs=7c count=1 , and then i used tr like this: cat myfile | tr [: xdigit:] '7'. Unfortunately it doesn't work. Please help me , thanks.

---

