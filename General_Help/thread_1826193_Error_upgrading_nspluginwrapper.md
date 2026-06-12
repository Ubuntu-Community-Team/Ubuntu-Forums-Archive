---
title: "Error upgrading nspluginwrapper"
date: 2011-08-16
forum: General Help
---

### Post by kernco on 2011-08-16
I'm currently running Ubuntu 11.04, but I've had this problem on this machine for a while, before I upgraded to 11.04 and possibly before I had even switched to 10.10, I can't remember.

The problem is that whenever I upgrade packages, nspluginwrapper causes an error:
```
Setting up nspluginwrapper (1.2.2-0ubuntu9) ...
plugin dirs:
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
*** glibc detected *** nspluginwrapper: double free or corruption (out): 0x0000000001055150 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a8f)[0x7ff6ef388a8f]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x73)[0x7ff6ef38c8e3]
/lib/x86_64-linux-gnu/libdl.so.2(+0x1565)[0x7ff6ef6a5565]
/lib/x86_64-linux-gnu/libdl.so.2(dlsym+0x4a)[0x7ff6ef6a509a]
nspluginwrapper[0x4017e1]
nspluginwrapper[0x401902]
nspluginwrapper[0x401661]
nspluginwrapper[0x402f12]
nspluginwrapper[0x403b6f]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xff)[0x7ff6ef32eeff]
nspluginwrapper[0x401259]
======= Memory map: ========
00400000-00406000 r-xp 00000000 08:05 262223                             /usr/lib/nspluginwrapper/x86_64/linux/npconfig
00605000-00606000 r--p 00005000 08:05 262223                             /usr/lib/nspluginwrapper/x86_64/linux/npconfig
00606000-00607000 rw-p 00006000 08:05 262223                             /usr/lib/nspluginwrapper/x86_64/linux/npconfig
00607000-00608000 rw-p 00000000 00:00 0 
0103a000-0105b000 rw-p 00000000 00:00 0                                  [heap]
7ff6e8000000-7ff6e8021000 rw-p 00000000 00:00 0 
7ff6e8021000-7ff6ec000000 ---p 00000000 00:00 0 
7ff6ec790000-7ff6ec7a5000 r-xp 00000000 08:05 929557                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7ff6ec7a5000-7ff6ec9a4000 ---p 00015000 08:05 929557                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7ff6ec9a4000-7ff6ec9a5000 r--p 00014000 08:05 929557                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7ff6ec9a5000-7ff6ec9a6000 rw-p 00015000 08:05 929557                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7ff6ec9a6000-7ff6eca2a000 r-xp 00000000 08:05 927558                     /lib/x86_64-linux-gnu/libm-2.13.so
7ff6eca2a000-7ff6ecc29000 ---p 00084000 08:05 927558                     /lib/x86_64-linux-gnu/libm-2.13.so
7ff6ecc29000-7ff6ecc2a000 r--p 00083000 08:05 927558                     /lib/x86_64-linux-gnu/libm-2.13.so
7ff6ecc2a000-7ff6ecc2b000 rw-p 00084000 08:05 927558                     /lib/x86_64-linux-gnu/libm-2.13.so
7ff6ecc2b000-7ff6ecd13000 r-xp 00000000 08:05 540230                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7ff6ecd13000-7ff6ecf12000 ---p 000e8000 08:05 540230                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7ff6ecf12000-7ff6ecf1a000 r--p 000e7000 08:05 540230                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7ff6ecf1a000-7ff6ecf1c000 rw-p 000ef000 08:05 540230                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7ff6ecf1c000-7ff6ecf31000 rw-p 00000000 00:00 0 
7ff6ee211000-7ff6ee26e000 r-xp 00000000 08:05 681852                     /opt/google/talkplugin/libnpgoogletalk64.so
7ff6ee26e000-7ff6ee46e000 ---p 0005d000 08:05 681852                     /opt/google/talkplugin/libnpgoogletalk64.so
7ff6ee46e000-7ff6ee472000 rw-p 0005d000 08:05 681852                     /opt/google/talkplugin/libnpgoogletalk64.so
7ff6ee472000-7ff6ee47e000 r-xp 00000000 08:05 928056                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7ff6ee47e000-7ff6ee67d000 ---p 0000c000 08:05 928056                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7ff6ee67d000-7ff6ee67e000 r--p 0000b000 08:05 928056                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7ff6ee67e000-7ff6ee67f000 rw-p 0000c000 08:05 928056                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7ff6ee67f000-7ff6ee68a000 r-xp 00000000 08:05 928059                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7ff6ee68a000-7ff6ee889000 ---p 0000b000 08:05 928059                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7ff6ee889000-7ff6ee88a000 r--p 0000a000 08:05 928059                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7ff6ee88a000-7ff6ee88b000 rw-p 0000b000 08:05 928059                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7ff6ee88b000-7ff6ee8a2000 r-xp 00000000 08:05 928048                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7ff6ee8a2000-7ff6eeaa1000 ---p 00017000 08:05 928048                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7ff6eeaa1000-7ff6eeaa2000 r--p 00016000 08:05 928048                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7ff6eeaa2000-7ff6eeaa3000 rw-p 00017000 08:05 928048                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7ff6eeaa3000-7ff6eeaa5000 rw-p 00000000 00:00 0 
7ff6eeaa5000-7ff6eeaad000 r-xp 00000000 08:05 928049                     /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7ff6eeaad000-7ff6eecac000 ---p 00008000 08:05 928049                     /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7ff6eecac000-7ff6eecad000 r--p 00007000 08:05 928049                     /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7ff6eecad000-7ff6eecae000 rw-p 00008000 08:05 928049                     /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7ff6eecae000-7ff6eecc6000 r-xp 00000000 08:05 928115                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7ff6eecc6000-7ff6eeec6000 ---p 00018000 08:05 928115                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7ff6eeec6000-7ff6eeec7000 r--p 00018000 08:05 928115                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7ff6eeec7000-7ff6eeec8000 rw-p 00019000 08:05 928115                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7ff6eeec8000-7ff6eeecc000 rw-p 00000000 00:00 0 
7ff6eeecc000-7ff6eeed3000 r-xp 00000000 08:05 928209                     /lib/x86_64-linux-gnu/librt-2.13.so
7ff6eeed3000-7ff6ef0d2000 ---p 00007000 08:05 928209                     /lib/x86_64-linux-gnu/librt-2.13.so
7ff6ef0d2000-7ff6ef0d3000 r--p 00006000 08:05 928209                     /lib/x86_64-linux-gnu/librt-2.13.so
7ff6ef0d3000-7ff6ef0d4000 rw-p 00007000 08:05 928209                     /lib/x86_64-linux-gnu/librt-2.13.so
7ff6ef0d4000-7ff6ef10f000 r-xp 00000000 08:05 929572                     /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7ff6ef10f000-7ff6ef30e000 ---p 0003b000 08:05 929572                     /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7ff6ef30e000-7ff6ef30f000 r--p 0003a000 08:05 929572                     /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7ff6ef30f000-7ff6ef310000 rw-p 0003b000 08:05 929572                     /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7ff6ef310000-7ff6ef49a000 r-xp 00000000 08:05 927368                     /lib/x86_64-linux-gnu/libc-2.13.so
7ff6ef49a000-7ff6ef699000 ---p 0018a000 08:05 927368                     /lib/x86_64-linux-gnu/libc-2.13.so
7ff6ef699000-7ff6ef69d000 r--p 00189000 08:05 927368                     /lib/x86_64-linux-gnu/libc-2.13.so
7ff6ef69d000-7ff6ef69e000 rw-p 0018d000 08:05 927368                     /lib/x86_64-linux-gnu/libc-2.13.so
7ff6ef69e000-7ff6ef6a4000 rw-p 00000000 00:00 0 Aborted
dpkg: error processing nspluginwrapper (--configure):
 subprocess installed post-installation script returned error exit status 134
Errors were encountered while processing:
 nspluginwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How can I get this working again? I've tried removing (with remove and purge) and reinstalling, but still getting the error.

---

### Post by kernco on 2011-09-28
I still haven't been able to fix this issue.

---

### Post by dcstar on 2011-09-29
> **kernco said:**
> 
.........
How can I get this working again? I've tried removing (with remove and purge) and reinstalling, but still getting the error.

Clear the cache files as well.

---

### Post by gandaran on 2011-09-29
why do you need nspluginwrapper? is it for running 32-bits flash on 64-bits Ubuntu? if correct then I recommend removing nspluginwrapper and the installed flash then get 64-bits adobe flash installed instead.

---

