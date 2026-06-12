---
title: "Creating bytes"
date: 2011-12-08
forum: General Help
---

### Post by nickyflavian on 2011-12-08
Hey. Recently I was wondering if it is possible to create let's say 22 bytes of 25 or 8 bytes of 7, and so on. I now that using the dd command ,i.e. dd if=/dev/zero of=/whatever_file  bs=...  count=.., let's you create a number of zero bytes or  using /dev/random instead of /dev/zero for generatig randomly bytes. But how to create 22 bytes of 25 or 8 bytes of 7? If anybody knows please post here.

---

### Post by The Cog on 2011-12-08
I can't think how to do it without writing a program. I tried to use **dd** to pipe some of /dev/zero through **tr** but I couldn't work out how to get tr to translate zero bytes. Any other byte, no problem, but not zero bytes.

So here's a python program:
```
#!/usr/bin/env python
import sys
try:
    charcount = int(sys.argv[1])
    charval = int(sys.argv[2])
    sys.stdout.write(chr(charval) * charcount)
except:
    print "Make a number of bytes"
    print "Usage: %s bytecount bytevalue" % sys.argv[0]

```
save it in a file (for this example call it makebytes).
Make it executable: chmod +x makebytes
Use it like this - to output 10 bytes of value 120:
> ./makebytes 10 120

---

