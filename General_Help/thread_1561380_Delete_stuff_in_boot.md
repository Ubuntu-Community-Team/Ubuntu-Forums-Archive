---
title: "Delete stuff in /boot"
date: 2010-08-26
forum: General Help
---

### Post by t0p on 2010-08-26
I've no free disk space and I've been following guides up the wazoo to get some back.  I just looked at /boot, and this is what it looks like:

```

t0p@deimos:~$ ls -l /boot
total 62740
-rw-r--r-- 1 root root  528310 2009-11-11 11:54 abi-2.6.28-16-generic
-rw-r--r-- 1 root root  528372 2009-12-01 21:04 abi-2.6.28-17-generic
-rw-r--r-- 1 root root  528420 2010-03-12 06:48 abi-2.6.28-18-generic
-rw-r--r-- 1 root root  528356 2010-07-28 05:04 abi-2.6.28-19-generic
-rw-r--r-- 1 root root  504555 2009-02-23 23:07 abi-2.6.29-1-netbook
-rw-r--r-- 1 root root   96866 2009-11-11 11:54 config-2.6.28-16-generic
-rw-r--r-- 1 root root   96866 2009-12-01 21:04 config-2.6.28-17-generic
-rw-r--r-- 1 root root   96866 2010-03-12 06:48 config-2.6.28-18-generic
-rw-r--r-- 1 root root   96866 2010-07-28 05:04 config-2.6.28-19-generic
-rw-r--r-- 1 root root   89946 2009-02-23 23:07 config-2.6.29-1-netbook
drwxr-xr-x 2 root root    4096 2010-08-06 18:42 grub
-rw-r--r-- 1 root root 7613242 2009-11-25 10:46 initrd.img-2.6.28-16-generic
-rw-r--r-- 1 root root 7612876 2009-12-05 10:37 initrd.img-2.6.28-17-generic
-rw-r--r-- 1 root root 7612505 2010-03-17 00:50 initrd.img-2.6.28-18-generic
-rw-r--r-- 1 root root 7612500 2010-08-06 18:42 initrd.img-2.6.28-19-generic
-rw-r--r-- 1 root root 6119000 2009-07-19 19:32 initrd.img-2.6.29-1-netbook
-rw-r--r-- 1 root root  128796 2009-03-27 17:15 memtest86+.bin
-rw-r--r-- 1 root root 1450875 2009-11-11 11:54 System.map-2.6.28-16-generic
-rw-r--r-- 1 root root 1450875 2009-12-01 21:04 System.map-2.6.28-17-generic
-rw-r--r-- 1 root root 1450810 2010-03-12 06:48 System.map-2.6.28-18-generic
-rw-r--r-- 1 root root 1450807 2010-07-28 05:04 System.map-2.6.28-19-generic
-rw-r--r-- 1 root root 1462685 2009-02-23 23:07 System.map-2.6.29-1-netbook
-rw-r--r-- 1 root root    1074 2009-11-11 11:56 vmcoreinfo-2.6.28-16-generic
-rw-r--r-- 1 root root    1074 2009-12-01 21:06 vmcoreinfo-2.6.28-17-generic
-rw-r--r-- 1 root root    1074 2010-03-12 06:50 vmcoreinfo-2.6.28-18-generic
-rw-r--r-- 1 root root    1074 2010-07-28 05:06 vmcoreinfo-2.6.28-19-generic
-rw-r--r-- 1 root root    1075 2009-02-23 23:08 vmcoreinfo-2.6.29-1-netbook
-rw-r--r-- 1 root root 3491824 2009-11-11 11:54 vmlinuz-2.6.28-16-generic
-rw-r--r-- 1 root root 3491600 2009-12-01 21:04 vmlinuz-2.6.28-17-generic
-rw-r--r-- 1 root root 3491024 2010-03-12 06:48 vmlinuz-2.6.28-18-generic
-rw-r--r-- 1 root root 3491664 2010-07-28 05:04 vmlinuz-2.6.28-19-generic
-rw-r--r-- 1 root root 2997872 2009-02-23 23:07 vmlinuz-2.6.29-1-netbook

```

See all that stuff referring to Lady knows what past kernels?  The only kernels I (think I) have on board are 2.6.28-19 and 2.6.29-1.  Can I delete the rest?  How?  A simple *rm* command or is there some utility I need to use?

Thanks.

---

### Post by plucky on 2010-08-26
> See all that stuff referring to Lady knows what past kernels? The only kernels I (think I) have on board are 2.6.28-19 and 2.6.29-1. Can I delete the rest? How? A simple rm command or is there some utility I need to use?


Open Synaptic Package Manager and search for ```
linux-image
``` and mark for complete removal will clear out /boot.

You can also search for ```
linux-headers
``` and also remove.

It is good to leave the current kernel and one other in case the current one breaks.

Good Luck

---

### Post by wojox on 2010-08-26
This is what I use [Ubucleaner - Simple bash script to keep your Ubuntu System Clean]("http://www.ubuntugeek.com/ubucleaner-simple-bash-script-to-keep-your-ubuntu-system-clean.html")

It will clean up everything but your current kernel.

---

### Post by t0p on 2010-08-26
Thanks, that worked wonderfully.

---

