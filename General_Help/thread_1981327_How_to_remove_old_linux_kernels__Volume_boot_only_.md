---
title: "How to remove old linux kernels / Volume boot only has 6MB remaining"
date: 2012-05-16
forum: General Help
---

### Post by agrayray on 2012-05-16
Today I run some updated on my 10.4 32 bit Ubuntu computer and got error saying my boot volume only has 6MB remaining....through a little searching I found some pages that said I can delete old ones which I tried with command 

sudo apt-get remove linux-image.2.6.32.generic but got that it wasnt there...

below is dump from the console showing whats in my /boot and the command I entered...can someone please pass on what is the proper command to remove this or advice on how I correct this?

Thanks!

rei@rei-ubuntu:~$ ls -lah /boot
total 195M
drwxr-xr-x  4 root root 5.0K 2012-05-16 15:43 .
drwxr-xr-x 22 rei  rei  4.0K 2012-05-16 15:43 ..
-rw-r--r--  1 root root 626K 2010-04-16 09:01 abi-2.6.32-21-generic
-rw-r--r--  1 root root 626K 2010-06-03 21:56 abi-2.6.32-22-generic
-rw-r--r--  1 root root 637K 2010-06-11 08:53 abi-2.6.32-23-generic
-rw-r--r--  1 root root 637K 2010-09-16 14:14 abi-2.6.32-24-generic
-rw-r--r--  1 root root 637K 2010-10-16 19:46 abi-2.6.32-25-generic
-rw-r--r--  1 root root 637K 2010-11-24 08:57 abi-2.6.32-26-generic
-rw-r--r--  1 root root 637K 2010-12-01 19:48 abi-2.6.32-27-generic
-rw-r--r--  1 root root 637K 2011-01-10 20:18 abi-2.6.32-28-generic
-rw-r--r--  1 root root 637K 2011-02-11 14:56 abi-2.6.32-29-generic
-rw-r--r--  1 root root 637K 2011-03-01 21:27 abi-2.6.32-30-generic
-rw-r--r--  1 root root 637K 2011-04-08 19:35 abi-2.6.32-31-generic
-rw-r--r--  1 root root 637K 2011-04-20 18:52 abi-2.6.32-32-generic
-rw-r--r--  1 root root 638K 2011-09-13 20:51 abi-2.6.32-34-generic
-rw-r--r--  1 root root 638K 2012-04-27 23:39 abi-2.6.32-41-generic
-rw-r--r--  1 root root 114K 2010-04-16 09:01 config-2.6.32-21-generic
-rw-r--r--  1 root root 114K 2010-06-03 21:56 config-2.6.32-22-generic
-rw-r--r--  1 root root 114K 2010-06-11 08:53 config-2.6.32-23-generic
-rw-r--r--  1 root root 114K 2010-09-16 14:14 config-2.6.32-24-generic
-rw-r--r--  1 root root 114K 2010-10-16 19:46 config-2.6.32-25-generic
-rw-r--r--  1 root root 114K 2010-11-24 08:57 config-2.6.32-26-generic
-rw-r--r--  1 root root 114K 2010-12-01 19:48 config-2.6.32-27-generic
-rw-r--r--  1 root root 114K 2011-01-10 20:18 config-2.6.32-28-generic
-rw-r--r--  1 root root 114K 2011-02-11 14:56 config-2.6.32-29-generic
-rw-r--r--  1 root root 114K 2011-03-01 21:27 config-2.6.32-30-generic
-rw-r--r--  1 root root 114K 2011-04-08 19:35 config-2.6.32-31-generic
-rw-r--r--  1 root root 114K 2011-04-20 18:52 config-2.6.32-32-generic
-rw-r--r--  1 root root 114K 2011-09-13 20:51 config-2.6.32-34-generic
-rw-r--r--  1 root root 114K 2012-04-27 23:39 config-2.6.32-41-generic
drwxr-xr-x  3 root root 7.0K 2012-05-16 15:45 grub
-rw-r--r--  1 root root 7.6M 2010-05-11 06:27 initrd.img-2.6.32-21-generic
-rw-r--r--  1 root root 7.6M 2010-06-05 17:00 initrd.img-2.6.32-22-generic
-rw-r--r--  1 root root 7.6M 2010-07-03 06:56 initrd.img-2.6.32-23-generic
-rw-r--r--  1 root root 7.6M 2010-09-18 23:45 initrd.img-2.6.32-24-generic
-rw-r--r--  1 root root 7.6M 2010-11-11 06:33 initrd.img-2.6.32-25-generic
-rw-r--r--  1 root root 7.6M 2010-12-20 20:47 initrd.img-2.6.32-26-generic
-rw-r--r--  1 root root 7.6M 2011-02-02 14:19 initrd.img-2.6.32-27-generic
-rw-r--r--  1 root root 7.6M 2011-02-11 23:22 initrd.img-2.6.32-28-generic
-rw-r--r--  1 root root 7.6M 2011-03-21 19:37 initrd.img-2.6.32-29-generic
-rw-r--r--  1 root root 7.6M 2011-04-05 19:03 initrd.img-2.6.32-30-generic
-rw-r--r--  1 root root 7.6M 2011-05-08 22:03 initrd.img-2.6.32-31-generic
-rw-r--r--  1 root root 7.6M 2011-05-30 11:03 initrd.img-2.6.32-32-generic
-rw-r--r--  1 root root 7.7M 2011-10-18 16:45 initrd.img-2.6.32-34-generic
-rw-r--r--  1 root root 7.7M 2012-05-16 15:43 initrd.img-2.6.32-41-generic
drwx------  2 root root  12K 2010-05-11 06:16 lost+found
-rw-r--r--  1 root root 157K 2010-03-23 05:37 memtest86+.bin
-rw-r--r--  1 root root 1.7M 2010-04-16 09:01 System.map-2.6.32-21-generic
-rw-r--r--  1 root root 1.7M 2010-06-03 21:56 System.map-2.6.32-22-generic
-rw-r--r--  1 root root 1.7M 2010-06-11 08:53 System.map-2.6.32-23-generic
-rw-r--r--  1 root root 1.7M 2010-09-16 14:14 System.map-2.6.32-24-generic
-rw-r--r--  1 root root 1.7M 2010-10-16 19:46 System.map-2.6.32-25-generic
-rw-r--r--  1 root root 1.7M 2010-11-24 08:57 System.map-2.6.32-26-generic
-rw-r--r--  1 root root 1.7M 2010-12-01 19:48 System.map-2.6.32-27-generic
-rw-r--r--  1 root root 1.7M 2011-01-10 20:18 System.map-2.6.32-28-generic
-rw-r--r--  1 root root 1.7M 2011-02-11 14:56 System.map-2.6.32-29-generic
-rw-r--r--  1 root root 1.7M 2011-03-01 21:27 System.map-2.6.32-30-generic
-rw-r--r--  1 root root 1.7M 2011-04-08 19:35 System.map-2.6.32-31-generic
-rw-r--r--  1 root root 1.7M 2011-04-20 18:52 System.map-2.6.32-32-generic
-rw-r--r--  1 root root 1.7M 2011-09-13 20:51 System.map-2.6.32-34-generic
-rw-r--r--  1 root root 1.7M 2012-04-27 23:39 System.map-2.6.32-41-generic
-rw-r--r--  1 root root 1.2K 2010-04-16 09:03 vmcoreinfo-2.6.32-21-generic
-rw-r--r--  1 root root 1.2K 2010-06-03 21:58 vmcoreinfo-2.6.32-22-generic
-rw-r--r--  1 root root 1.2K 2010-06-11 08:56 vmcoreinfo-2.6.32-23-generic
-rw-r--r--  1 root root 1.2K 2010-09-16 14:16 vmcoreinfo-2.6.32-24-generic
-rw-r--r--  1 root root 1.2K 2010-10-16 19:47 vmcoreinfo-2.6.32-25-generic
-rw-r--r--  1 root root 1.2K 2010-11-24 09:00 vmcoreinfo-2.6.32-26-generic
-rw-r--r--  1 root root 1.2K 2010-12-01 19:50 vmcoreinfo-2.6.32-27-generic
-rw-r--r--  1 root root 1.2K 2011-01-10 20:20 vmcoreinfo-2.6.32-28-generic
-rw-r--r--  1 root root 1.2K 2011-02-11 14:57 vmcoreinfo-2.6.32-29-generic
-rw-r--r--  1 root root 1.2K 2011-03-01 21:29 vmcoreinfo-2.6.32-30-generic
-rw-r--r--  1 root root 1.2K 2011-04-08 19:38 vmcoreinfo-2.6.32-31-generic
-rw-r--r--  1 root root 1.2K 2011-04-20 18:54 vmcoreinfo-2.6.32-32-generic
-rw-r--r--  1 root root 1.2K 2011-09-13 20:53 vmcoreinfo-2.6.32-34-generic
-rw-r--r--  1 root root 1.2K 2012-04-27 23:40 vmcoreinfo-2.6.32-41-generic
-rw-r--r--  1 root root 3.9M 2010-04-16 09:01 vmlinuz-2.6.32-21-generic
-rw-r--r--  1 root root 3.9M 2010-06-03 21:56 vmlinuz-2.6.32-22-generic
-rw-r--r--  1 root root 3.9M 2010-06-11 08:53 vmlinuz-2.6.32-23-generic
-rw-r--r--  1 root root 3.9M 2010-09-16 14:14 vmlinuz-2.6.32-24-generic
-rw-r--r--  1 root root 3.9M 2010-10-16 19:46 vmlinuz-2.6.32-25-generic
-rw-r--r--  1 root root 3.9M 2010-11-24 08:57 vmlinuz-2.6.32-26-generic
-rw-r--r--  1 root root 3.9M 2010-12-01 19:48 vmlinuz-2.6.32-27-generic
-rw-r--r--  1 root root 3.9M 2011-01-10 20:18 vmlinuz-2.6.32-28-generic
-rw-r--r--  1 root root 3.9M 2011-02-11 14:56 vmlinuz-2.6.32-29-generic
-rw-r--r--  1 root root 3.9M 2011-03-01 21:27 vmlinuz-2.6.32-30-generic
-rw-r--r--  1 root root 3.9M 2011-04-08 19:35 vmlinuz-2.6.32-31-generic
-rw-r--r--  1 root root 3.9M 2011-04-20 18:52 vmlinuz-2.6.32-32-generic
-rw-r--r--  1 root root 3.9M 2011-09-13 20:51 vmlinuz-2.6.32-34-generic
-rw-r--r--  1 root root 3.9M 2012-04-27 23:39 vmlinuz-2.6.32-41-generic
rei@rei-ubuntu:~$ sudo apt-get remove linux-image.2.6.32.21-generic
[sudo] password for rei: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image.2.6.32.21-generic
rei@rei-ubuntu:~$ uname -srv
Linux 2.6.32-41-generic #89-Ubuntu SMP Fri Apr 27 22:22:09 UTC 2012
rei@rei-ubuntu:~$

---

### Post by cmont899 on 2012-05-16
try this:

```
sudo dpkg --purge linux-image.2.6.32.21-generic
```

---

### Post by pbrane on 2012-05-16
This is a better way to list all installed kernels.
```

dpkg -l | grep -iE 'linux-image|linux-headers' | awk '{print $2}'

```
This way you will know the name of the packages to remove.

... as an example...
```

sudo apt-get purge linux-image-2.6.32-21-generic

```

---

### Post by agrayray on 2012-05-16
Thanks all...it worked very nicely and now I removed many of the old kernels I dont need and all fixed!!!

Thanks again!!!

---

