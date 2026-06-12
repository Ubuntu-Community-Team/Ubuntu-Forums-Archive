---
title: "Help with /boot"
date: 2012-05-27
forum: General Help
---

### Post by bartho12 on 2012-05-27
I am being advised that the /boot partition is full. I have removed all old kernel packages and it seems to not have changes the space utilization. It almost seems like there are hidden files.

When I run "ls -l -h /boot" i get the following:

mike@Media-Server:~$ ls -l -h /boot
total 15M
-rw-r--r-- 1 root root 641K 2012-02-13 20:16 abi-2.6.32-39-generic-pae
-rw-r--r-- 1 root root 114K 2012-02-13 20:16 config-2.6.32-39-generic-pae
drwxr-xr-x 3 root root 4.0K 2012-05-27 12:29 grub
-rw-r--r-- 1 root root 8.4M 2012-03-06 06:33 initrd.img-2.6.32-39-generic-pae
drwxr-xr-x 2 root root  12K 2010-09-30 07:15 lost+found
-rw-r--r-- 1 root root 1.7M 2012-02-13 20:16 System.map-2.6.32-39-generic-pae
-rw-r--r-- 1 root root 1.2K 2012-02-13 20:17 vmcoreinfo-2.6.32-39-generic-pae
-rw-r--r-- 1 root root 4.0M 2012-02-13 20:16 vmlinuz-2.6.32-39-generic-pae

However, then I run "df -h" it shows over 211M is being uses
mike@Media-Server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             228M  211M  4.9M  98% /boot

Any thoughts on what I can do to free up space in /boot and why there is a utilization discrepancy?

Thanks in advance!

---

### Post by The Cog on 2012-05-27
It might be in one of those two subdirectiories. Try this command:
```
sudo du -sh /boot/*
```
Also, there might be hidden files, so 
```
ls -al /boot
```
might show something

---

### Post by bartho12 on 2012-05-27
That did not really reveil anything.

mike@Media-Server:~$ sudo du -sh /boot/*
[sudo] password for mike: 
645K	/boot/abi-2.6.32-39-generic-pae
115K	/boot/config-2.6.32-39-generic-pae
4.0M	/boot/grub
8.4M	/boot/initrd.img-2.6.32-39-generic-pae
12K	/boot/lost+found
1.7M	/boot/System.map-2.6.32-39-generic-pae
2.0K	/boot/vmcoreinfo-2.6.32-39-generic-pae
4.1M	/boot/vmlinuz-2.6.32-39-generic-pae


mike@Media-Server:~$ ls -al /boot
total 15153
drwxr-xr-x  5 root root    4096 2012-05-27 12:22 .
drwxr-xr-x 26 root root    4096 2012-05-27 12:22 ..
-rw-r--r--  1 root root  656085 2012-02-13 20:16 abi-2.6.32-39-generic-pae
-rw-r--r--  1 root root  116469 2012-02-13 20:16 config-2.6.32-39-generic-pae
drwxr-xr-x  3 root root    4096 2012-05-27 12:29 grub
-rw-r--r--  1 root root 8732471 2012-03-06 06:33 initrd.img-2.6.32-39-generic-pae
drwxr-xr-x  2 root root   12288 2010-09-30 07:15 lost+found
-rw-r--r--  1 root root 1734310 2012-02-13 20:16 System.map-2.6.32-39-generic-pae
drwx------  4 root root    1024 2012-02-15 18:58 .Trash-0
-rw-r--r--  1 root root    1200 2012-02-13 20:17 vmcoreinfo-2.6.32-39-generic-pae
-rw-r--r--  1 root root 4181888 2012-02-13 20:16 vmlinuz-2.6.32-39-generic-pae

---

### Post by drs305 on 2012-05-27
It did reveal you have a .Trash-0 folder. It could contain files taking up space. Delete the file by opening a file browser as root and use **SHIFT-DEL** to remove the .Trash-0 folder.

```
gksu nautilus /boot
```
CTRL-h if the hidden files aren't visible at first.

---

### Post by bartho12 on 2012-05-27
Deleting the trash folder resolved the problem. Thanks for the help!!

---

