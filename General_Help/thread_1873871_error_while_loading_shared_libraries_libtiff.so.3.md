---
title: "error while loading shared libraries: libtiff.so.3:"
date: 2011-11-02
forum: General Help
---

### Post by rasmus91 on 2011-11-02
Hi.

I need to install Maya 2012 (on my 64 bit system). Which I did, everything went along just fine. until i tried running it with the maya command.

This is what I get:

```
rasmus@rasmus-Aspire-5745G:~$ maya
/usr/autodesk/maya2012-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

```

I tried this to make it work.
```
rasmus@rasmus-Aspire-5745G:~$ sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
[sudo] password for rasmus: 
ln: creating symbolic link `/usr/lib/libtiff.so.3': File exists

```

what can I do?

---

### Post by rasmus91 on 2011-11-02
So I tried linking to the libtiff.so.4 in /usr/lib32 instead. but the i get this:

```
rasmus@rasmus-Aspire-5745G:~$ maya
/usr/autodesk/maya2012-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: wrong ELF class: ELFCLASS32

```

then i found this: [http://ubuntuforums.org/showthread.php?t=1778013]("http://ubuntuforums.org/showthread.php?t=1778013")

and tried this:

```
rasmus@rasmus-Aspire-5745G:~$ sudo -i
[sudo] password for rasmus: 
root@rasmus-Aspire-5745G:~# cd /usr/lib
root@rasmus-Aspire-5745G:/usr/lib# ldconfig -v |grep libtiff
/sbin/ldconfig.real: Can't stat /lib/i686-linux-gnu: No such file or directory
/sbin/ldconfig.real: Can't stat /usr/lib/i686-linux-gnu: No such file or directory
/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Cannot stat /usr/lib32/libasprintf.so: No such file or directory
	libtiff.so.4 -> libtiff.so.4.3.4
	libtiff.so.4 -> libtiff.so.4.3.4
	libtiff.so.4 -> libtiff.so.4.3.4
	libtiff.so.4 -> libtiff.so.3 (changed)

```

i just dont get this...

---

### Post by jkapsi on 2011-11-08
Well I had the same problem. I solved it by deleting the link to libtiff.so.3 and the by running from terminal:

```
    sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/libtiff.so.3
```

It's a problem appeared when I upgraded to ubuntu 11.10. It seems that in ubuntu 11.10 the library changed from libtiff.so.4 to libtiff.4.3.4

---

