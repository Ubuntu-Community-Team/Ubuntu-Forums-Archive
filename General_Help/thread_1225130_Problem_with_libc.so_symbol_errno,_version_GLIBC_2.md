---
title: "Problem with libc.so: symbol errno, version GLIBC_2.0 not defined"
date: 2009-07-28
forum: General Help
---

### Post by juliangl on 2009-07-28
Dear experts,
I have Ubuntu Jaunty installed here and want to run a (unfortunately non-public) private software, which was compiled in a very old Linux/GCC environment. Unfortunately when running I get the error message:
./grope_motif.run 
./grope_motif.run: relocation error: ./grope_motif.run: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
I assume this is due to the fact that while compiling a version of libc that is a lot older was used. 
Is there any way to "install" the right library or point the program to the right library?
I appreciate any help
Julian

Perhaps the following output can help you
$ ldd grope_motif.run
        linux-gate.so.1 =>  (0xb7f15000)
        libXm.so.1 => /usr/lib/libXm.so.1 (0xb7dfb000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7da8000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7d97000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb7d8e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c9f000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7c86000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7c54000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c50000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c29000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ac6000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7abd000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7ab9000)
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7a9f000)
        /lib/ld-linux.so.2 (0xb7f16000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7a86000)
        libuuid.so.1 => /lib/libuuid.so.1 (0xb7a81000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7a7c000)
The library /lib/tls/i686/cmov/libc.so.6 is a link to libc-2.9.so and executing it leads to
$ /lib/tls/i686/cmov/libc.so.6
GNU C Library stable release version 2.9, by Roland McGrath et al.
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.3.3.
Compiled on a Linux >>2.6.24-23-server<< system on 2009-04-09.
Available extensions:
        crypt add-on version 2.1 by Michael Glad and others
        GNU Libidn by Simon Josefsson
        Native POSIX Threads Library by Ulrich Drepper et al
        BIND-8.2.3-T5B
For bug reporting instructions, please see:
<http://www.gnu.org/software/libc/bugs.html>.

---

