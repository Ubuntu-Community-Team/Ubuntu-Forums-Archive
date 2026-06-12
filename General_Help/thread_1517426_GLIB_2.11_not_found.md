---
title: "GLIB_2.11 not found"
date: 2010-06-25
forum: General Help
---

### Post by kvramya on 2010-06-25
I am using ubuntu lucid 10.04 64-bit.
I am trying to install libc6_2.7-10ubuntu6_amd64.deb by dpkg. But I get the following error.

```
/bin/sh: /lib/libc.so.6: version `GLIBC_2.11' not found (required by /bin/sh)
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/bin/sh: /lib/libc.so.6: version `GLIBC_2.11' not found (required by /bin/sh)
dpkg: error processing libc6_2.7-10ubuntu6_amd64.deb (--install):
 subprocess new post-removal script returned error exit status 1
/bin/sh: /lib/libc.so.6: version `GLIBC_2.11' not found (required by /bin/sh)


```The ldd output is 
```

ldd -v /bin/sh
    linux-vdso.so.1 =>  (0x00007fff58912000)
    libc.so.6 => /lib/libc.so.6 (0x00007f508c928000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f508ccb9000)

    Version information:
    /bin/sh:
        libc.so.6 (GLIBC_2.4) => /lib/libc.so.6
        libc.so.6 (GLIBC_2.3) => /lib/libc.so.6
        libc.so.6 (GLIBC_2.3.4) => /lib/libc.so.6
        libc.so.6 (GLIBC_2.11) => /lib/libc.so.6
        libc.so.6 (GLIBC_2.2.5) => /lib/libc.so.6
    /lib/libc.so.6:
        ld-linux-x86-64.so.2 (GLIBC_PRIVATE) => /lib64/ld-linux-x86-64.so.2
        ld-linux-x86-64.so.2 (GLIBC_2.3) => /lib64/ld-linux-x86-64.so.2

```How to solve this ? 

Thanks in advance
--
Ramya

---

### Post by VH-BIL on 2010-06-25
Check this thread out:
[*_[SOLVED] `GLIBC_2.11' not found (required by /bin/sh)_*]("http://ubuntuforums.org/showthread.php?t=1508725")

---

### Post by kvramya on 2010-06-25
> **VH-BIL said:**
> Check this thread out:
[*_[SOLVED] `GLIBC_2.11' not found (required by /bin/sh)_*]("http://ubuntuforums.org/showthread.php?t=1508725")

Hey, thanks for the reply. I have seen that thread.

But there even ldd was not installed. Its not so in my case. And the thread looks for a complete reinstall. I am looking for a solution without a complete re-install

--
Ramya

---

### Post by VH-BIL on 2010-06-25
You can try get the file from a rpm search if you can't find a deb and convert it to a deb with alien.
like:
[http://www.rpmfind.net/linux/rpm2html/search.php?query=libc.so.6(GLIBC_2.11)(64bit](http://www.rpmfind.net/linux/rpm2html/search.php?query=libc.so.6(GLIBC_2.11)(64bit))
[http://rpm.pbone.net/index.php3/stat/3/srodzaj/1/search/libc.so.6(GLIBC_2.11)(64bit](http://rpm.pbone.net/index.php3/stat/3/srodzaj/1/search/libc.so.6(GLIBC_2.11)(64bit))

---

### Post by Bachstelze on 2010-06-25
Why for heaven's sake do you want to install another libc6 version? It seems to me that you really don't know what you are doing here.

---

### Post by VH-BIL on 2010-06-25
> **Bachstelze said:**
> Why for heaven's sake do you want to install another libc6 version? It seems to me that you really don't know what you are doing here.

I was under the impression the file was missing and he could not get the file.

---

### Post by kvramya on 2010-06-25
> **Bachstelze said:**
> Why for heaven's sake do you want to install another libc6 version? It seems to me that you really don't know what you are doing here.

When was installing vim by dpkg, it showed that I do not have the libc6 and hence had to try installing it.

---

### Post by VH-BIL on 2010-06-25
Search for libc6 in synaptic, it is there.

---

