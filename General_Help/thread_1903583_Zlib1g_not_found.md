---
title: "Zlib1g not found"
date: 2012-01-02
forum: General Help
---

### Post by davidsrsb on 2012-01-02
I am having problems compiling programs that need zlib1g. I have both zlib1g and zlib1g-dev installed.
I get these errors:
 fontdata.c: (.text.startup+0x55): undefined reference to `gzopen'
 fontdata.c: (.text.startup+0xc4): undefined reference to `gzgetc'
 fontdata.c: (.text.startup+0x15a): undefined reference to `gzclose'

If I select zlib1g is Synaptic I and look at Installed Files I get:
"The list of installed files is only available for installed packages"
The zlib1g-dev package does list several files.

---

### Post by davidsrsb on 2012-01-04
SOLVED 11.10 is more fussy about compiler flag positions. This worked
#	cc -Wall -O2 -lz -fomit-frame-pointer fontdata.c -o fontdata
	cc -Wall -O2 -fomit-frame-pointer fontdata.c -lz -o fontdata
see how -lz is moved
and
#	cc -Wall -O2 -fomit-frame-pointer -lm bearing.c -o bearing
	cc -Wall -O2 -fomit-frame-pointer bearing.c -lm -o bearing
The -lm has to move for the math library to be found

---

