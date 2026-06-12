---
title: "Ubuntu 10.04 - missing &quot;Build&quot; directory for current kernel | 2.6.32-38-generic |"
date: 2012-02-17
forum: General Help
---

### Post by floorripper on 2012-02-17
Hello guys,

I was trying to install a some wireless compact drivers, and I figured out, that my build directory is somehow missing.

Do you know how can I get that directory back, or copy it from another computer where it is? On my another linux pc with the same kernel it is present.

majo@laptop:/lib/modules/2.6.32-38-generic$ pwd
**/lib/modules/2.6.32-38-generic**

So this directory is missing on my home laptop:
**[COLOR=DeepSkyBlue]lrwxrwxrwx  1 root root     40 2012-01-24 13:22 build -> /usr/src/linux-headers-2.6.32-38-generic/[/COLOR]**


@laptop:/lib/modules/2.6.32-38-generic$ ll
total 3860
drwxr-xr-x  5 root root   4096 2012-01-24 13:23 ./
drwxr-xr-x  8 root root   4096 2012-01-24 13:22 ../
lrwxrwxrwx  1 root root     40 2012-01-24 13:22 build -> /usr/src/linux-headers-2.6.32-38-generic/
drwxr-xr-x  2 root root   4096 2012-01-24 13:22 initrd/
drwxr-xr-x 10 root root   4096 2012-01-24 13:22 kernel/
-rw-r--r--  1 root root 618545 2012-01-24 13:23 modules.alias
-rw-r--r--  1 root root 596526 2012-01-24 13:23 modules.alias.bin
-rw-r--r--  1 root root   5084 2012-01-04 15:22 modules.builtin
-rw-r--r--  1 root root   6363 2012-01-24 13:23 modules.builtin.bin
-rw-r--r--  1 root root     69 2012-01-24 13:23 modules.ccwmap
-rw-r--r--  1 root root 270852 2012-01-24 13:23 modules.dep
-rw-r--r--  1 root root 399262 2012-01-24 13:23 modules.dep.bin
-rw-r--r--  1 root root   1405 2012-01-24 13:23 modules.ieee1394map
-rw-r--r--  1 root root    218 2012-01-24 13:23 modules.inputmap
-rw-r--r--  1 root root  24886 2012-01-24 13:23 modules.isapnpmap
-rw-r--r--  1 root root     74 2012-01-24 13:23 modules.ofmap
-rw-r--r--  1 root root 104668 2012-01-04 15:22 modules.order
-rw-r--r--  1 root root 407779 2012-01-24 13:23 modules.pcimap
-rw-r--r--  1 root root   1597 2012-01-24 13:23 modules.seriomap
-rw-r--r--  1 root root 229162 2012-01-24 13:23 modules.symbols
-rw-r--r--  1 root root 295996 2012-01-24 13:23 modules.symbols.bin
-rw-r--r--  1 root root 925642 2012-01-24 13:23 modules.usbmap
drwxr-xr-x  3 root root   4096 2012-01-24 13:23 updates/



majo@laptop:~$ cat /etc/issue
Ubuntu 10.04.3 LTS \n \l


majo@laptop:~$ uname -r
[B]2.6.32-38-generic
[/B]

Thanks,

---

