---
title: "Using dd command to write bytes"
date: 2010-12-19
forum: General Help
---

### Post by dgs012 on 2010-12-19
I'm using
```
dd if=/dev/zero bs=5 count=1 of=binfile
```Then I run

```
hexdump -b binfile
``` 0000000 000 000 000 000 000 

How can I use dd to write bytes of 1 or 5 for example?
hexdump -b will return
0000000 001 001 001 001 001
or
0000000 005 005 005 005 005

---

