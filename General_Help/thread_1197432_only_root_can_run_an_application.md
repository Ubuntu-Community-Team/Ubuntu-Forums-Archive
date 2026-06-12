---
title: "only root can run an application"
date: 2009-06-26
forum: General Help
---

### Post by jeszi on 2009-06-26
Hello,

I have an application that can use only with root. If I try to run this application with a normal user I had "killed" message.

Here is the history:

```

root@idc1as15:~# file /eas/all/bin/CAGENT
/eas/all/bin/CAGENT: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped
root@idc1as15:~# ldd /eas/all/bin/CAGENT
	linux-gate.so.1 =>  (0xb7f67000)
	libncurses.so.5 => /lib/libncurses.so.5 (0xb7f31000)
	libcobrts.so => /opt/microfocus/developer/lib/libcobrts.so (0xb7eb2000)
	libcobcrtn.so => /opt/microfocus/developer/lib/libcobcrtn.so (0xb7e74000)
	libcobmisc.so => /opt/microfocus/developer/lib/libcobmisc.so (0xb7e52000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d03000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7cff000)
	libcobscreen.so => /opt/microfocus/developer/lib/libcobscreen.so (0xb7cf7000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7cd1000)
	/lib/ld-linux.so.2 (0xb7f68000)
root@idc1as15:~# /eas/all/bin/CAGENT
IRPCOB: Aufrufparameter falsch
root@idc1as15:~# su -l valaki ldd /eas/all/bin/CAGENT
	not a dynamic executable
root@idc1as15:~# su -l valaki /eas/all/bin/CAGENT
/eas/all/bin/CAGENT: /eas/all/bin/CAGENT: cannot execute binary file
root@idc1as15:~# su - valaki
valaki@idc1as15:~$ /eas/all/bin/CAGENT
Killed
root@idc1as15:~# uname -a
Linux idc1as15 2.6.24-24-server #1 SMP Wed Apr 15 16:36:01 UTC 2009 i686 GNU/Linux

```

System: Ubuntu 8.04.2 LTS

Probably it is a permission problem. But I really don't know.

Help me please. :confused:

---

### Post by lisati on 2009-06-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jeszi on 2009-06-26
RESOLVED

The binary file need to be able to access low mmap addresses.
These were disabled in recent Linux kernels in order to try and avoid 
certain kinds of NULL pointer bugs causing problems.

Solution:
"echo 0 > /proc/sys/vm/mmap_min_addr"

---

