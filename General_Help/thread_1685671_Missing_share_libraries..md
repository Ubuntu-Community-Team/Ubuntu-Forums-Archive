---
title: "Missing share libraries."
date: 2011-02-11
forum: General Help
---

### Post by vasco.debian on 2011-02-11
Hi,

I am using Ubuntu 10.04 (32-Bit) Desktop edition.
Trying to install Citrix receiver as per instructions given [here]("http://support.citrix.com/article/CTX125285").

Getting following error when trying start applications.

```

sameer@sameer-desktop:~$ /usr/lib/ICAClient/wfcmgr 
/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory
```

Libraries already installed/setup as per instructions.
```
sameer@sameer-desktop:~$ sudo ln -s /usr/lib/libXm.so.3 /usr/lib/libXm.so.4

```
However ldconfig is able to find required libraries.

```
sameer@sameer-desktop:~$  sudo ldconfig -v | grep Xm.so.3
        libXm.so.3 -> libXm.so.4


sameer@sameer-desktop:~$ ldd /usr/lib/ICAClient/wfcmgr 
        linux-gate.so.1 =>  (0xf779a000)
        [COLOR="Red"]libXm.so.4 => not found[/COLOR]
        libXp.so.6 => /usr/lib32/libXp.so.6 (0xf7776000)
        libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf7764000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf775b000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7742000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf772b000)
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7727000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7723000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7709000)
        libc.so.6 => /lib32/libc.so.6 (0xf75af000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf755c000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf743f000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf742f000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf742b000)
        libuuid.so.1 => /lib32/libuuid.so.1 (0xf7425000)
        /lib/ld-linux.so.2 (0xf779b000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf740b000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7405000)
```

---

### Post by Perfect Storm on 2011-02-11
You're using 64-bit. If you look it's looking for 32-bit libs in /usr/lib32

You need to install the libXm.so.4 32-bit lib manually to /usr/lib32

---

### Post by vasco.debian on 2011-02-11
Thanks for bringing that to attention.
:o

---

