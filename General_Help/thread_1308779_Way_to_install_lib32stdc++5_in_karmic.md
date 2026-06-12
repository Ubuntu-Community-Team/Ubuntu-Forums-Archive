---
title: "Way to install lib32stdc++5 in karmic?"
date: 2009-10-31
forum: General Help
---

### Post by RhysU on 2009-10-31
To use the Intel 10.1 compilers on a 64-bit system, I need a 32-bit version of libstdc++5.  This sits in the package lib32stdc++5 which is not available in karmic.  lib32stdc++6 is available but doesn't work for the Intel 10.1 binaries.

How can I install lib32stdc++5 in karmic?

---

### Post by klemes on 2009-10-31
```
sudo cp libstdc++.so.5 /usr/lib32/
```

---

### Post by RhysU on 2009-11-01
> sudo cp libstdc++.so.5 /usr/lib32/

Really?  That seems suspect as /usr/lib/libstdc++.so.5 library is clearly the 64-bit version on my 64-bit system:
```
libstdc++.so.5.0.7: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```

Trying out your command and then checking the result of ldd on the 32-bit Intel compiler binary shows that the 64-bit version definitely won't cut it.

---

### Post by klemes on 2009-11-01
I am sorry but I am using also 64bit Karmic and I have no libstdc++.so.5 in /usr/lib.
For me just dropping the 32bit version that I found somewhere in the net in the /usr/lib32 directory did the trick and I was able to use the program that needed it which incidentally was not from the official  reposotories.

:popcorn:

---

### Post by RhysU on 2009-11-01
Yeah, I resorted to just picking it up from Jaunty and dropping it in place.  I threw together a quick write up: [http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html]("http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html").

Thanks all for the help.

---

