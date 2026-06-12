---
title: "UPX compressed executables causing problems?"
date: 2010-04-02
forum: General Help
---

### Post by johncc330 on 2010-04-02
Hello people,

First off, I'm not an Ubuntu user, but many of my students are. 

I just circulated a first term exam, for which they had to use a compiler from my page, 
and they reported they couldn't run it. The compiler exited without any message at all. 
I asked for an strace, and from the result started suspecting the UPX compressor.
Doing a search on the 'net for that coincidence, I found quite a few cases of failures
(epsxe is one of those reported on the Ubuntu forums).

I suggested they try decompressing and then running - that worked. 

So, why doesn't Ubuntu accept UPX compacted executables? And, particularly
worrysome, why doesn't Ubuntu show a reason for not wanting to execute?

John

(The student reports came from systems with 9.10 installed).

---

### Post by johncc330 on 2010-04-06
Please, can anyone indicate me how to solve the UPX problem with Ubuntu?

---

### Post by meonkeys on 2010-04-07
Try this. If you see a "corrupted section header size" message, or something similar, like:

```
$ file /path/to/executable
/path/to/executable: ELF 32-bit LSB executable, Intel 80386, version 1, statically linked, corrupted section header size
```

Try uncompressing the binary permanently, as follows:
```
$ sudo apt-get install upx-ucl
$ upx -d /path/to/executable
```

sudo may be necessary for the "upx" command, depending on owner/permissions for the executable.

Hope this helps,
-Adam

---

