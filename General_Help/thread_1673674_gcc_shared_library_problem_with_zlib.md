---
title: "gcc shared library problem with zlib"
date: 2011-01-22
forum: General Help
---

### Post by mr.miles on 2011-01-22
Hi, I can't use gcc until I fix a problem with zlib, but I'm stuck. Please help.

The symptom:```

miles@miles-desktop:~$ gcc
/usr/bin/gcc: error while loading shared libraries: libz.so.1: cannot open shared object file: Error 24
```

This happened after I uninstalled and then reinstalled gcc using synaptic.
I tried reinstalling gcc, glib1z (provides zlib), and build-essentials, but gcc gives the same error.

I tried running ldconfig, which didn't fix the problem:
```
miles@miles-desktop:/var/cache/apt/archives$ sudo ldconfig -v |grep libz
/sbin/ldconfig.real: Can't stat /lib/x86_64-linux-gnu: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libportaudiocpp.so: No such file or directory
	libz.so.1 -> libz.so.1.2.3.3
	libzephyr.so.4 -> libzephyr.so.4.0.0
	libz.so.1 -> libz.so.1.2.3.3
miles@miles-desktop:/var/cache/apt/archives$ 
```

here's the output of ldd:
```
miles@miles-desktop:~$ ldd /usr/bin/gcc
	linux-vdso.so.1 =>  (0x00007fff93fff000)
	libz.so.1 => /lib/libz.so.1 (0x00007fb9a166f000)
	libc.so.6 => /lib/libc.so.6 (0x00007fb9a12ec000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fb9a18aa000)
```

 libz.so.1 is in /lib:```

miles@miles-desktop:~$ ls -l /lib/libz.so.1
lrwxrwxrwx 1 root root 15 2011-01-22 12:44 /lib/libz.so.1 -> libz.so.1.2.3.3
miles@miles-desktop:~$ ls -l /lib/libz.so.1.2.3.3 
-rw-r--r-- 1 root root 92752 2009-11-10 00:53 /lib/libz.so.1.2.3.3
```

---

### Post by mr.miles on 2011-01-23
Here's a workaround that let me compile stuff again:

install package gcc-4.3
change symlink for /usr/bin/gcc to point to gcc-4.3

---

### Post by gmargo on 2011-01-23
What version OS?  What version compiler?

gcc on 10.10 Maverick or 10.04 Lucid does not link to libz.

---

### Post by mr.miles on 2011-01-23
I'm running Ubuntu 10.04 LTS.

When I run ldd, it says that gcc-4.4 needs libz.so.1 but gcc-4.3 doesn't.

```
miles@miles-desktop:~/src/flightgear2$ ldd /usr/bin/gcc-4.3
	linux-vdso.so.1 =>  (0x00007fffafbf2000)
	libc.so.6 => /lib/libc.so.6 (0x00007f692dc29000)
miles@miles-desktop:~/src/flightgear2$ ldd /usr/bin/gcc-4.4
	linux-vdso.so.1 =>  (0x00007fff621fa000)
	libz.so.1 => /lib/libz.so.1 (0x00007f5087364000)
	libc.so.6 => /lib/libc.so.6 (0x00007f5086fe1000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f50875a1000)
```

---

### Post by gmargo on 2011-01-23
That is strange.  My 10.04 Lucid gcc does not link to libz at all.

```

$ lsb_release  -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:        10.04
Codename:       lucid

$ gcc --version | head -1
gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3

$ ls -l /usr/bin/gcc*
lrwxrwxrwx 1 root root      7 Dec 29 08:21 /usr/bin/gcc -> gcc-4.4
-rwxr-xr-x 1 root root 255192 Mar 26  2010 /usr/bin/gcc-4.4

$ ldd /usr/bin/gcc-4.4
        linux-vdso.so.1 =>  (0x00007fff12fff000)
        libc.so.6 => /lib/libc.so.6 (0x00007f2936f1b000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f29372ad000)

```

---

### Post by mr.miles on 2011-01-23
I still can't check the shared object dependencies of gcc-4.4 cause I haven't fixed the problem yet.

This all happened because I installed ccache, and overwrote /usr/bin/gcc-4.4 by mistake. The shared library problem is probably a result of me 'customizing' files that ldconfig and maybe dpkg use.

I couldn't remove gcc because of something that looked like a circular package diversion, so I followed the instructions here and removed some lines from /var/lib/dpkg/diversions related to fglrx:
[URL="http://ubuntuforums.org/showthread.php?t=1579437"]Fglrx with Mobility Radeon 5870 - Error Installing
[/URL]
I removed some lines from /var/lib/dpkg/diversions, got fglrx removed, removed gcc, and reinstalled gcc-4.4, but afterwards I couldn't use gcc-4.4. Then I changed /etc/ld.so.conf, but I undid the changes I made there. I ran ldconfig a few times both ways, but that didn't seem to make a difference.

Just now I replaced /var/lib/dpkg/diversions that I edited with the backed-up version, and reinstalled gcc-4.4, but I still can't use gcc-4.4, so I linked gcc to gcc-4.3 again.



```

miles@miles-desktop:/usr/bin$ gcc-4.4
/usr/bin/gcc-4.4: error while loading shared libraries: libz.so.1: cannot open shared object file: Error 24

miles@miles-desktop:/usr/bin$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid
```

Also, reinstalling libc-bin and libc6 from synaptic didn't change the gcc-4.4 error.

---

