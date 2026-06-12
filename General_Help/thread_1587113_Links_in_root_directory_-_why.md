---
title: "Links in root directory - why?"
date: 2010-10-03
forum: General Help
---

### Post by Krupski on 2010-10-03
Hi all,


```

root@storage:/# ls -laF
total 92
drwxr-xr-x  20 root root  4096 2010-10-03 00:22 ./
drwxr-xr-x  20 root root  4096 2010-10-03 00:22 ../
drwxr-xr-x   2 root root  4096 2010-10-03 01:15 bin/
drwxr-xr-x   3 root root  4096 2010-10-02 14:31 boot/
drwxr-xr-x  17 root root  3820 2010-10-03 00:35 dev/
-rw-r--r--   1 root root  1445 2010-09-13 09:19 dq45cb.bios.ver.0127.13.sep.2010
drwxr-xr-x  92 root root  4096 2010-10-03 01:14 etc/
drwxr-xr-x   4 root root  4096 2010-10-02 22:51 home/
[COLOR="Red"][B]lrwxrwxrwx   1 root root    32 2010-10-02 14:18 initrd.img -> boot/initrd.img-2.6.32-25-server
lrwxrwxrwx   1 root root    32 2010-10-02 13:08 initrd.img.old -> boot/initrd.img-2.6.32-24-server[/B][/COLOR]
drwxr-xr-x  13 root root 12288 2010-10-02 14:17 lib/
lrwxrwxrwx   1 root root     4 2010-10-02 13:04 lib64 -> /lib/
drwx------   2 root root 16384 2010-10-02 13:03 lost+found/
drwxr-xr-x   2 root root  4096 2010-10-02 13:03 media/
drwxr-xr-x   2 root root  4096 2010-07-29 03:42 mnt/
drwxr-xr-x   2 root root  4096 2010-10-02 13:04 opt/
dr-xr-xr-x 187 root root     0 2010-10-02 10:21 proc/
-rw-------   1 root root  1024 2010-10-02 13:17 .rnd
drwx------   5 root root  4096 2010-10-03 01:04 root/
drwxr-xr-x   2 root root  4096 2010-10-02 14:19 sbin/
drwxr-xr-x   2 root root  4096 2010-10-02 13:04 srv/
drwxr-xr-x  13 root root     0 2010-10-02 10:21 sys/
drwxrwxrwt   5 root root   100 2010-10-03 01:12 tmp/
drwxr-xr-x  10 root root  4096 2010-10-02 13:04 usr/
drwxr-xr-x  14 root root  4096 2010-10-02 14:23 var/
[COLOR="Red"][B]lrwxrwxrwx   1 root root    29 2010-10-02 14:18 vmlinuz -> boot/vmlinuz-2.6.32-25-server
lrwxrwxrwx   1 root root    29 2010-10-02 13:08 vmlinuz.old -> boot/vmlinuz-2.6.32-24-server[/B][/COLOR]

```

The lines highlighted in red are symbolic links to the boot files. Yet, they are not used and, if deleted, the system still works.

Anyone know why they are there? Is it a leftover from Linux days gone by, or does SOMETHING use them?

Thanks!

-- Roger

---

### Post by andrewthomas on 2010-10-03
The links are used to boot a kernel without having to supply its full name.  

For example, in a rescue situation.

---

### Post by WorMzy on 2010-10-03
As far as I know, they always point to the newest kernel/initrd, so you can create a menu item in grub which uses them to always boot them, without having to run update-grub every time.

---

