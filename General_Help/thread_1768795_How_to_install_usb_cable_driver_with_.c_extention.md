---
title: "How to install usb cable driver with .c extention?"
date: 2011-05-27
forum: General Help
---

### Post by Julita on 2011-05-27
Hello! I have done the following (downloaded the driver to "serial" directory) :

1. cd /usr/src/linux-headers-2.6.31-14/drivers/usb/serial/
2. depmod -a
3. modprobe driver_name
I get FATAL error, Module not found, even though it's there. 

The driver is for my kernel version.

I appreciate any help.

---

### Post by Wim Sturkenboom on 2011-05-27
Files with '.c' extension are source files; you need to compile them with gcc. Check the directory where your source is for readme files, install and configure files.

---

### Post by Julita on 2011-05-27
Thank you for your advice, but there are no instructions. I have followed the pattern

```
gcc -Wall -DMODULE -D__KERNEL -DLINUX -I /usr/src/linux-headers-2.6.28-11/include -c sample2.c
```

but I still have errors. I am looking into the issue right now.

I have such errors as

```
/usr/src/linux-headers-2.6.31-14/include/linux/mod_devicetable.h:119: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
```

---

