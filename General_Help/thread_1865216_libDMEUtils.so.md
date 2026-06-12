---
title: "libDMEUtils.so??"
date: 2011-10-19
forum: General Help
---

### Post by captainentropy on 2011-10-19
OK, this is a long-shot to get this resolved. I'm trying to run some rpm based software on Ubuntu. I used Alien to convert the rpms to deb. No problem there really. I was able to install the deb package no problem either. But when I issue to command to run the executable I need nothing happens and I get this error: "bash: ./[executable]: No such file or directory" Now that's a silly error message because the file *is* there and has the right permissions. So I thought perhaps it had something to do with the software being 32-bit and my OS (Ubuntu 10.04) is 64-bit. Now this 32-bit software currently runs on a 64-bit CentOS so I know that by itself isn't' an issue. So I googled a bit and found a similar problem that required installing the libc6-i386 libraries. So I did that and got the following error "error while loading shared libraries: libDMEUtils.so: cannot open shared object file"

Of course I could be on the wrong path with the 32/64-bit thing anyway. But I googled that error and got nothing, literally. "libDMEUtils" also has zero results. 

So, does anyone have any idea libDMEUtils is or what it's a part of?

Thanks!

---

