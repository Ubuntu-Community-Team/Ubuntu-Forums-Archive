---
title: "libstdc++.so.5 exists but not found"
date: 2012-07-11
forum: General Help
---

### Post by davemar on 2012-07-11
I'm trying to run some software that relies on the libstdc++.so.5 library. As this is an old library (superceeded by libstdc++.so.6) I had to download it and installed it using dpkg.

It has appeared in the correct place:
```

lrwxrwxrwx 1 root root      18 2012-07-11 12:19 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root  829320 2010-11-02 22:16 /usr/lib/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root      19 2012-03-16 07:50 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r-- 1 root root 1044008 2012-03-09 04:20 /usr/lib/libstdc++.so.6.0.13

```

I've also done 'sudo ldconfig' to update that too (even though dpkg does that anyway).

But when I run the software I still get the error:
```
error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

Any ideas?

---

### Post by spjackson on 2012-07-11
Could it be that you are on a 64-bit platform and so dpkg has installed a 64-bit libstdc++.so.5 but your old program is 32-bit? What is reported by
```

file OldProgramNameHere
ldd OldProgramNameHere

```

---

### Post by davemar on 2012-07-11
I get:
```
ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, not stripped
```
and I'm on a 64-bit machine, so that explains it.
ldd gives:
```

	linux-gate.so.1 =>  (0xf76eb000)
	libstdc++.so.5 => not found
	libm.so.6 => /lib32/libm.so.6 (0xf76a0000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7681000)
	libc.so.6 => /lib32/libc.so.6 (0xf7528000)
	/lib/ld-linux.so.2 (0xf76ec000)

```

I can't install the i386 version of libstc++5 though, as dpkg gives this error:
```
package architecture (i386) does not match system (amd64)
```

Is there anyway around this?

---

### Post by spjackson on 2012-07-11
> **davemar said:**
> I can't install the i386 version of libstc++5 though, as dpkg gives this error:
```
package architecture (i386) does not match system (amd64)
```Is there anyway around this?
It seems that there isn't an official package that will install it in the right place (/usr/lib32).
However, here are a few links that tell you how to do it by hand.

[http://ubuntuforums.org/showthread.php?t=1282957](http://ubuntuforums.org/showthread.php?t=1282957)
[http://ashu-geek.blogspot.co.uk/2011/11/how-to-install-libstdcso5-on-ubuntu.html](http://ashu-geek.blogspot.co.uk/2011/11/how-to-install-libstdcso5-on-ubuntu.html)
[http://agentzlerich.blogspot.co.uk/2009/11/getting-32-bit-libstdcso5-in-karmic.html](http://agentzlerich.blogspot.co.uk/2009/11/getting-32-bit-libstdcso5-in-karmic.html)

---

### Post by davemar on 2012-07-13
Thanks for those links, that's led me to a solution:

```

dpkg-deb -x libstdc++5_3.3.6-20~lucid1_i386.deb tmp
sudo cp tmp/usr/lib/libstdc++.so.5.0.7 /usr/lib32/
cd /usr/lib32
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5
sudo ldconfig

```

which seems to work.

Thanks again for the help!

---

