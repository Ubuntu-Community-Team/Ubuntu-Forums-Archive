---
title: "Valgrind Test"
date: 2011-10-26
forum: General Help
---

### Post by newport_j on 2011-10-26
I think thta this is the correct section to put this question:
 
 
After performing the steps below I tried out Valgrind 3.6.1 installation as the instructions said to do. the first steps:
 
1. ./configure
 
2. make
 
3. make install
 
Now all of those worked fine, but then I performed the next step.
 
I typed "valgrind ls -l" and this is what I got as output:
 
 
```

[FONT=Times New Roman][SIZE=3]james@james-Precision-WorkStation-T7500:~/Desktop/valgrind-3.6.1$ valgrind ls -l[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]==18092== Memcheck, a memory error detector[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]==18092== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]==18092== Using Valgrind-3.6.1 and LibVEX; rerun with -h for copyright info[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]==18092== Command: ls -l[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]==18092== [/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]valgrind:  Fatal error at startup: a function redirection[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  which is mandatory for this platform-tool combination[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  cannot be set up.  Details of the redirection are:[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]valgrind:  [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]valgrind:  A must-be-redirected function[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  whose name matches the pattern:      index[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  in an object with soname matching:   ld-linux.so.2[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  was not found whilst processing[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  symbols from the object with soname: ld-linux.so.2[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]valgrind:  [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]valgrind:  Possible fixes: (1, short term): install glibc's debuginfo[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  package on this machine.  (2, longer term): ask the packagers[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  for your Linux distribution to please in future ship a non-[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  stripped ld.so (or whatever the dynamic linker .so is called)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  that exports the above-named function using the standard[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  calling conventions for this platform.  The package you need[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:  to install for fix (1) is called[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]valgrind:  [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]valgrind:    On Debian, Ubuntu:                 libc6-dbg[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind:    On SuSE, openSuSE, Fedora, RHEL:   glibc-debuginfo[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]valgrind:  [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]valgrind:  Cannot continue -- exiting now.  Sorry.[/SIZE][/FONT]
 

```
 
Now I am unsure as to what this means. It seems the install and configure went well, but the first command ("valgrind ls -l") failed and I got this paragraph of output.
 
How do I correct it?
 
Any help appreciated.
 
Thanks in advance.
 
Newport_j

---

### Post by newport_j on 2011-10-27
Ok, I think I know what I must do. I need to install some additonal software, but I cannot find it. I need to install
 
glibc-debuginfo 
 
in the current valgrind install. I can only find a rpm version, but this not an Ubuntu version. Where is there an Ubuntu version that I can install?
 
I need that one (the Ubuntu version) it is difficult to install an rpm version.
 
Thanks in advance.
 
Newport_j

---

### Post by talonmies on 2011-10-27
Why would you build valgrind from source, rather than just [install it]("https://wiki.ubuntu.com/Valgrind") from the package [repository]("http://packages.ubuntu.com/search?keywords=valgrind")? If you install it from the repository, all of the necessary dependencies will be installed automatically....

---

### Post by newport_j on 2011-10-27
Thus pc is not connected to the network or the internet. I must do it the harder way. I cannot use 
 
sudo apt-get ... 
 
There was no problem installing until the test command. Then I learned of this shortcoming. This glibc package needs to be installed. I must do it the hard way. If there is an easier way then please let me know.
 
I need to install it to get Valgrind to run.
 
Newport_j

---

### Post by talonmies on 2011-10-28
No. You can download all the packages (.deb files) you need and install them on locally on the machine without internet. The links I gave you shows all the dependencies each package requires. Download them, copy them to the non-networked machine and install them.

---

### Post by newport_j on 2011-10-31
I have downloaded the valgrind*.deb file and the libc6-dbg*.deb file. I have them on the harddrive of the non-networked pc.
 
What is the command to install?
 
There seems to be several, but I beleive that the one using dpkg is the only one that works in my situtaion. Again, the pc is stand alone, not network connected. 
 
 
Newport_j

---

### Post by newport_j on 2011-10-31
Okay, I used dpkg -i *deb and it installed. I used the Valgrind that I built and it gave what seemed to be the correct output. I used the build number which started this thread. I so no reason in install valgrind*.deb since I had built it already.
 
It seems to work - for now.
 
Newport_j

---

### Post by sleekweasel on 2011-11-03
Hi folks.

I'm seeing the same error message for a project which compiles with 4.5 under -m32: can't find index in ld-linux.so.2.

```

valgrind:  A must-be-redirected function
valgrind:  whose name matches the pattern:      index
valgrind:  in an object with soname matching:   ld-linux.so.2
valgrind:  was not found whilst processing
valgrind:  symbols from the object with soname: ld-linux.so.2

```

This worked before upgrade. I'm a bit stumped.

Is there a libc6-dbg for 32 bit?

I can successfully run valgrind ls -l.

I upgraded to Oneric a week or so ago, in advance of the other guys on my project, so I had to edit our makefiles to use gcc++-4.5 expressly (the upgrade left me with both 4.5 and 4.6 on my machine, with /usr/bin/g++ -> g++-4.6 without going through /etc/alternatives (!?)).

```
 dpkg -l|grep cpp
ii  cpp                                    4:4.6.1-2ubuntu5                           GNU C preprocessor (cpp)
ii  cpp-4.5                                4.5.3-9ubuntu1                             The GNU C preprocessor
ii  cpp-4.6                                4.6.1-9ubuntu3                             GNU C preprocessor
ii  libcppunit-1.12-1                      1.12.1-3                                   Unit Testing Library for C++
ii  libcppunit-dev                         1.12.1-3                                   Unit Testing Library for C++
ii  libcppunit-doc                         1.12.1-3                                   Unit Testing Library for C++

```
The first thing I tried to resolve the valgrind error was apt-get install libc6-dbg as valgrind suggested, followed by apt-get install valgrind to try to make sure it was up to date. Here's what I have now:

```
ii  valgrind                               1:3.6.1-0ubuntu3                           A memory debugger and profiler

ii  libc6                                  2.13-20ubuntu5                             Embedded GNU C Library: Shared libraries
ii  libc6:i386                             2.13-20ubuntu5                             Embedded GNU C Library: Shared libraries
ii  libc6-dbg                              2.13-20ubuntu5                             Embedded GNU C Library: detached debugging symbols
ii  libc6-dev                              2.13-20ubuntu5                             Embedded GNU C Library: Development Libraries and Header Files
ii  libc6-dev-i386                         2.13-20ubuntu5                             Embedded GNU C Library: 32-bit development libraries for AMD64
ii  libc6-i386                             2.13-20ubuntu5                             Embedded GNU C Library: 32-bit shared libraries for AMD64

```
My project runs happily without valgrind. Its ldd says:

```
        linux-gate.so.1 =>  (0xf7795000)
        libEGL.so => ../jni/PVRSDK/Builds/OGLES2/LinuxX86/Lib/libEGL.so (0xf7476000)
        libGLESv2.so => ../jni/PVRSDK/Builds/OGLES2/LinuxX86/Lib/libGLESv2.so (0xf71eb000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf70df000)
        libm.so.6 => /lib32/libm.so.6 (0xf70b5000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7097000)
        libc.so.6 => /lib32/libc.so.6 (0xf6f1d000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6de7000)
        librt.so.1 => /lib32/librt.so.1 (0xf6ddd000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf6dc2000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf6dbd000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6daa000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf6d9f000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6d96000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6d8a000)
        /lib/ld-linux.so.2 (0xf7796000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6d6b000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6d65000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6d61000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6d5a000)

```
with...

```
 ldd ../jni/PVRSDK/Builds/OGLES2/LinuxX86/Lib/libEGL.so
        linux-gate.so.1 =>  (0xf7711000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf729b000)
        librt.so.1 => /lib32/librt.so.1 (0xf7292000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7276000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7263000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf7258000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf724f000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7244000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7158000)
        libm.so.6 => /lib32/libm.so.6 (0xf712e000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7110000)
        libc.so.6 => /lib32/libc.so.6 (0xf6f96000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6f77000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf6f72000)
        /lib/ld-linux.so.2 (0xf7712000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6f6b000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6f67000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6f60000)

```
and... 
```

 ldd ../jni/PVRSDK/Builds/OGLES2/LinuxX86/Lib/libGLESv2.so
        linux-gate.so.1 =>  (0xf7794000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf73b0000)
        librt.so.1 => /lib32/librt.so.1 (0xf73a7000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf738b000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7378000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf736d000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf7364000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7359000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf726d000)
        libm.so.6 => /lib32/libm.so.6 (0xf7243000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7225000)
        libc.so.6 => /lib32/libc.so.6 (0xf70ab000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf708c000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7087000)
        /lib/ld-linux.so.2 (0xf7795000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf7080000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf707c000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7075000)

```

---

### Post by newport_j on 2011-11-04
The solution thta I used in clearly in the first message. I will repeat it here:
 
 
 
[FONT=Times New Roman][SIZE=3]The package you need[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind: to install for fix (1) is called[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]valgrind: [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]valgrind: On Debian, Ubuntu: libc6-dbg[/SIZE][/FONT]
 
 
 
This worked for me.
 
Newport_j

---

### Post by sleekweasel on 2011-11-08
Hi.

Thanks, but I already have that installed - it was listed in the set of libc packages above, and when I try installing it I get this confirmation:

```
sudo apt-get install libc6-dbg
[sudo] password for tim: 
Sorry, try again.
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6-dbg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```
Also
```

sudo apt-get install valgrind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
valgrind is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

I now notice the same error obtains if I build with 4.6, so... something's decidedly screwy.

It seems there's something else going on. :(

---

### Post by sleekweasel on 2011-11-16
I thought to run valgrind under strace:

```

write(1026, "==7935== Using Valgrind-3.6.1-De"..., 82==7935== Using Valgrind-3.6.1-Debian and LibVEX; rerun with -h for copyright info
) = 82
getpid()                                = 7935
write(1026, "==7935== Command: ./Debug/ShLyri"..., 38==7935== Command: ./Debug/ShLyricUnit
) = 38
getpid()                                = 7935
write(1026, "==7935== \n", 10==7935== 
)          = 10
mmap2(0x4620000, 500000, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, 0, 0) = 0x4620000
mmap2(0x469b000, 1048576, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, 0, 0) = 0x469b000
stat64("/lib/i386-linux-gnu/ld-2.13.so", {st_mode=S_IFREG|0755, st_size=126152, ...}) = 0
open("/lib/i386-linux-gnu/ld-2.13.so", O_RDONLY|O_LARGEFILE) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\20\0\0004\0\0\0"..., 1024) = 1024
close(3)                                = 0
stat64("/lib/i386-linux-gnu/ld-2.13.so", {st_mode=S_IFREG|0755, st_size=126152, ...}) = 0
open("/lib/i386-linux-gnu/ld-2.13.so", O_RDONLY|O_LARGEFILE) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\20\0\0004\0\0\0"..., 1024) = 1024
close(3)                                = 0
open("/lib/i386-linux-gnu/ld-2.13.so", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0755, st_size=126152, ...}) = 0
mmap2(0x479b000, 126152, PROT_READ, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x479b000
fstat64(3, {st_mode=S_IFREG|0755, st_size=126152, ...}) = 0
readlink("/proc/self/fd/3", "/lib/i386-linux-gnu/ld-2.13.so", 4096) = 30
close(3)                                = 0
open("/usr/lib/debug/.build-id/14/5c3b70bb10f6c00123ce420441885a02bb160c.debug", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/ld-2.13.so", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0755, st_size=126152, ...}) = 0
mmap2(0x47ba000, 126152, PROT_READ, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x47ba000
fstat64(3, {st_mode=S_IFREG|0755, st_size=126152, ...}) = 0
readlink("/proc/self/fd/3", "/lib/i386-linux-gnu/ld-2.13.so", 4096) = 30
close(3)                                = 0
munmap(0x47ba000, 126976)               = 0
open("/lib/i386-linux-gnu/.debug/ld-2.13.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/debug/lib/i386-linux-gnu/ld-2.13.so", O_RDONLY) = -1 ENOENT (No such file or directory)
munmap(0x479b000, 126976)               = 0
write(1026, "\n", 1
)                    = 1
write(1026, "valgrind:  Fatal error at startu"..., 58valgrind:  Fatal error at startup: a function redirection

```

I presume the 

```

open("/usr/lib/debug/lib/i386-linux-gnu/ld-2.13.so", O_RDONLY) = -1 ENOENT (No such file or directory)

```

is the problem - there's a /usr/lib/debug/lib/x86_64-linux-gnu/ld-2.13.so file, but no i386.

I have a 32-bit Natty chroot. Installing libc6-dbg there gave me this missing file. Copying that to my 64-bit installation allowed it to open the file, but it still complained in much the same way:

```

open("/lib/i386-linux-gnu/.debug/ld-2.13.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/debug/lib/i386-linux-gnu/ld-2.13.so", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0755, st_size=572832, ...}) = 0
mmap2(0x47ba000, 572832, PROT_READ, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x47ba000
fstat64(3, {st_mode=S_IFREG|0755, st_size=572832, ...}) = 0
readlink("/proc/self/fd/3", "/usr/lib/debug/lib/i386-linux-gnu/ld-2.13.so", 4096) = 44
close(3)                                = 0
munmap(0x47ba000, 573440)               = 0
munmap(0x479b000, 126976)               = 0
write(1026, "\n", 1
)                    = 1
write(1026, "valgrind:  Fatal error at startu"..., 58valgrind:  Fatal error at startup: a function redirection
) = 58

```


happily, I find I can simply run valgrind in the natty chroot.

Since I have a solution I'm not going to pursue this for now, but it seems to me that valgrind for 32 bit is broken on Oneric 64 because:

```

$ /chroot32/bin/ls
foo

```
but
```

$ valgrind /chroot32/bin/ls
==15949== Memcheck, a memory error detector
==15949== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==15949== Using Valgrind-3.6.1-Debian and LibVEX; rerun with -h for copyright info
==15949== Command: /chroot32/bin/ls
==15949== 

valgrind:  Fatal error at startup: a function redirection
valgrind:  which is mandatory for this platform-tool combination
valgrind:  cannot be set up.  Details of the redirection are:
valgrind:  
valgrind:  A must-be-redirected function
valgrind:  whose name matches the pattern:      index
valgrind:  in an object with soname matching:   ld-linux.so.2
valgrind:  was not found whilst processing
valgrind:  symbols from the object with soname: ld-linux.so.2
valgrind:  
valgrind:  Possible fixes: (1, short term): install glibc's debuginfo
valgrind:  package on this machine.  (2, longer term): ask the packagers
valgrind:  for your Linux distribution to please in future ship a non-
valgrind:  stripped ld.so (or whatever the dynamic linker .so is called)
valgrind:  that exports the above-named function using the standard
valgrind:  calling conventions for this platform.  The package you need
valgrind:  to install for fix (1) is called
valgrind:  
valgrind:    On Debian, Ubuntu:                 libc6-dbg
valgrind:    On SuSE, openSuSE, Fedora, RHEL:   glibc-debuginfo
valgrind:  
valgrind:  Cannot continue -- exiting now.  Sorry.


```

---

### Post by sleekweasel on 2011-11-16
This has been reported already:

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/881236]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/881236")

Workaround - being careful not to clobber any existing files:

download from [http://packages.ubuntu.com/oneiric/i386/libc6-dbg/download](http://packages.ubuntu.com/oneiric/i386/libc6-dbg/download)
```

$ dpkg-deb -X libc6-dbg_2.13-20ubuntu5_i386.deb /tmp
$ cp -r /tmp/usr/lib/debug/lib/i386-linux-gnu /usr/lib/debug/lib/i386-linux-gnu

```

---

