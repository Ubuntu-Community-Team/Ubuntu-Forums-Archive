---
title: "How To: Install Lexmark All-In-Ones"
date: 2010-04-01
forum: General Help
---

### Post by wbar2 on 2010-04-01
EDIT: This thread has been moved to the tutorials section: [http://ubuntuforums.org/showthread.php?p=9211584](http://ubuntuforums.org/showthread.php?p=9211584)

---

### Post by NCLI on 2010-04-01
You should post this in either [the Lucid forum]("http://ubuntuforums.org/forumdisplay.php?f=377") or [the Tutorials and Tips forum]("http://ubuntuforums.org/forumdisplay.php?f=100") ;)

---

### Post by wbar2 on 2010-04-01
Oh thanks! I was looking for that! I've put it tutorial and tips and am waiting for moderator approval.

---

### Post by Bob_G7 on 2010-04-02
Trying this on the Ubuntu Server, followed the instructions but when I try:

```
bash lexmark-08z-series-driver-1.0-1.i386.rpm.sh
```I get this as Administrator and root:

```
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
Error: Couldn't find any suitable frontend for your system
```Anyone have any idea what I'm missing?

Thanks in advance

---

### Post by wbar2 on 2010-04-02
I think you may be missing some more 32-bit libraries (maybe a difference since you are running the server edition).

This might solve your problem to help you find what 32-bit libs you are missing:
[http://ubuntuforums.org/showpost.php?p=7893634&postcount=8](http://ubuntuforums.org/showpost.php?p=7893634&postcount=8)

Just modify the file name for the one you are using (probably lexmark-08z-series-driver-1.0-1.i386.deb.sh).

---

### Post by wbar2 on 2010-04-09
I just installed Lucid Beta 2 32-bit, and libstdc++5 was not required. Instructions can now be found here in the Tutorials section:
[http://ubuntuforums.org/showthread.php?t=1444847](http://ubuntuforums.org/showthread.php?t=1444847)

---

### Post by ramesh7a77u on 2010-04-26
nkjet-09-driver-1.0-1.i386.deb.sh' 
Verifying archive integrity... All good.
Uncompressing nixstaller.........................................................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
TRACKING IDENT = 140509
cpu speed = 1050 MHz
ram size = 3708.1640625 MB
hd avail = 259824 MB
dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
dell-inkjet-09-driver-1.0-1.i386.deb

---

### Post by comthre3 on 2010-04-27
Finally got it working after a a couple of Lua errors. Thanks

---

