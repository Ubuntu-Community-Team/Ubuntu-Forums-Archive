---
title: "OpenGL Segmentation Fault"
date: 2010-10-24
forum: General Help
---

### Post by maedhros777 on 2010-10-24
I'm running Ubuntu 10.04, and for some reason I get a segfault whenever running programs with OpenGL. I ran "lspci | grep VGA" in the terminal and this is the output:

```
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
```Any help would be greatly appreciated.

---

### Post by Masiosare on 2010-11-30
Bump. Same here. Started happening today.

$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series


$ glxinfo 
name of display: :0.0
Segmentation fault


Using the radeon driver.

running glxinfo thru strace breaks around here:

readlink("/proc/self/exe", "/usr/bin/glxinfo", 8192) = 16
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\7\6\0\17\0\0\0", 8}, {"ATIFGLEXTENSION", 15}, {"\0", 1}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x1c9fa14, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Segmentation fault

Any pointers?

---

### Post by maedhros777 on 2010-12-28
I actually found the solution to my problem, just needed to disable the FGLRX driver and restart ([http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1625108](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1625108)). Not sure about your problem though.

---

