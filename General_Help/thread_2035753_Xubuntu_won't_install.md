---
title: "Xubuntu won't install"
date: 2012-07-31
forum: General Help
---

### Post by yoreei on 2012-07-31
Hello! When I try to install Xubuntu from a USB stick the installer doesn't show any signs of progress. I waited it for an hour but it still shows "Saving installed packages..."
Here is what the console-like thing underneath it displays:

```
Jul 31 12:10:06 xubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jul 31 12:10:06 xubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jul 31 12:10:06 xubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jul 31 12:10:06 xubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jul 31 12:10:06 xubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Jul 31 12:10:06 xubuntu 83haiku: debug: /dev/sda6 is not a BeFS partition: exiting
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jul 31 12:10:06 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jul 31 12:10:06 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda7
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jul 31 12:10:07 xubuntu 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jul 31 12:10:07 xubuntu 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jul 31 12:10:07 xubuntu macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jul 31 12:10:07 xubuntu 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jul 31 12:10:07 xubuntu 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Jul 31 12:10:07 xubuntu 83haiku: debug: /dev/sda7 is not a BeFS partition: exiting
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jul 31 12:10:07 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jul 31 12:10:07 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda8
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jul 31 12:10:08 xubuntu 10freedos: debug: /dev/sda8 is not a FAT partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jul 31 12:10:08 xubuntu 10qnx: debug: /dev/sda8 is not a QNX4 partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jul 31 12:10:08 xubuntu macosx-prober: debug: /dev/sda8 is not an HFS+ partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jul 31 12:10:08 xubuntu 20microsoft: debug: /dev/sda8 is not a MS partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jul 31 12:10:08 xubuntu 30utility: debug: /dev/sda8 is not a FAT partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Jul 31 12:10:08 xubuntu 83haiku: debug: /dev/sda8 is not a BeFS partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda9

** (ubiquity:3960): CRITICAL **: unable to create '/root/.cache/dconf'; dconf will not work properly.
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jul 31 12:10:08 xubuntu 10freedos: debug: /dev/sda9 is not a FAT partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jul 31 12:10:08 xubuntu 10qnx: debug: /dev/sda9 is not a QNX4 partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jul 31 12:10:08 xubuntu macosx-prober: debug: /dev/sda9 is not an HFS+ partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jul 31 12:10:08 xubuntu 20microsoft: debug: /dev/sda9 is not a MS partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jul 31 12:10:08 xubuntu 30utility: debug: /dev/sda9 is not a FAT partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Jul 31 12:10:08 xubuntu 83haiku: debug: /dev/sda9 is not a BeFS partition: exiting
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jul 31 12:10:08 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu 10freedos: debug: /dev/sdb1 is a FAT32 partition
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu 20microsoft: debug: /dev/sdb1 is a FAT32 partition
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu 30utility: debug: /dev/sdb1 is a FAT32 partition
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Jul 31 12:10:08 xubuntu ubiquity[3960]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Jul 31 12:10:08 xubuntu ubiquity[3960]: Step_before = stepWebcam
```Thank you in advance!

---

### Post by Laiquendi on 2012-07-31
I have found a bug with this critical error but it has been fixed.
Are you configuring your partitions properly? It seems like there is something messed up with the partitioning.

---

### Post by yoreei on 2012-07-31
Well, since now I have always installed linux distributions with only the / file system because I used to be a windows user and all these /usr /tmp /var and such seemed too confusing for me to configure so I sticked with the easy way - one partition for everything. This is my first time I've tried separating /var /tmp and /home onto their own partitions so it is very likely that I have messed something up. Here is a picture of how I have configured my HDD: 

[IMG]http://i.minus.com/ixVfGQaopxFQk.png[/IMG]

---

### Post by yoreei on 2012-07-31
You were right. I installed Xubuntu with only the / partition. Everything ran flawlessly. Thanks!

---

