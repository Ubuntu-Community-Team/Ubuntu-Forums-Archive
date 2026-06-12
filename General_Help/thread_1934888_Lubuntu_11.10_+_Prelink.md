---
title: "Lubuntu 11.10 + Prelink"
date: 2012-03-03
forum: General Help
---

### Post by sppo71 on 2012-03-03
Prelink does not lubuntu 11.10 version. There will be this kind of error message when you run as root symbols / etc / cron.daily / prelink

```
/etc/cron.daily/prelink: line 55:  1491 Aborted                  /usr/sbin/prelink -a $PRELINK_OPTS >> /var/log/prelink.log  2>&1
```and

```
/usr/sbin/prelink -a -mR -T -f
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/dd: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/readlink: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/nuke: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/minips: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/true: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/uname: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/dmesg: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/run-init: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/cpio: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mkfifo: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mkdir: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/insmod: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/sh.shared: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/kinit.shared: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/false: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/ipconfig: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/nfsmount: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/halt: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/reboot: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/chroot: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/kill: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/losetup: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/ln: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/sleep: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/pivot_root: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/ls: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/resume: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/cat: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/umount: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/fstype: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/poweroff: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mknod: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mount: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/sync: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
prelink.bin: ../../src/conflict.c:763: prelink_build_conflicts: Assertion `j < ndeps' failed.
Prelink failed with return value 134
```How do I get prelink to work properly?

---

### Post by sppo71 on 2012-03-03
> **sppo71 said:**
> Prelink does not lubuntu 11.10 version. There will be this kind of error message when you run as root symbols / etc / cron.daily / prelink

```
/etc/cron.daily/prelink: line 55:  1491 Aborted                  /usr/sbin/prelink -a $PRELINK_OPTS >> /var/log/prelink.log  2>&1
```and

```
/usr/sbin/prelink -a -mR -T -f
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/dd: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/readlink: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/nuke: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/minips: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/true: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/uname: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/dmesg: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/run-init: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/cpio: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mkfifo: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mkdir: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/insmod: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/sh.shared: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/kinit.shared: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/false: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/ipconfig: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/nfsmount: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/halt: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/reboot: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/chroot: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/kill: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/losetup: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/ln: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/sleep: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/pivot_root: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/ls: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/resume: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/cat: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/umount: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/fstype: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/poweroff: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mknod: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/mount: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
2012-02-28 17:49:46 prelink: /usr/lib/klibc/bin/sync: Using /lib/klibc-VpXo3NLt74O9YRk0FPMfZUIWwEU.so, not /lib/ld-linux.so.2 as dynamic linker
prelink.bin: ../../src/conflict.c:763: prelink_build_conflicts: Assertion `j < ndeps' failed.
Prelink failed with return value 134
```How do I get prelink to work properly?

bumb

---

### Post by raja.genupula on 2012-03-03
have you tried this 

[http://ubuntuforums.org/showthread.php?t=1801423](http://ubuntuforums.org/showthread.php?t=1801423)
[http://duopetalflower.blogspot.in/2010/07/enabling-prelink-in-ubuntu-lucid-like.html](http://duopetalflower.blogspot.in/2010/07/enabling-prelink-in-ubuntu-lucid-like.html)

---

### Post by tempusfuoit on 2012-03-05
I just posted a solution to your problem. This has been irritating me for sometime. Also, from  the Debian forums it looks like the package maintainer is AWOL. I would like to thank the Arch Linux community for their excellent documentaion that helped me figure this out.
 
[https://bugs.launchpad.net/ubuntu/+source/prelink/+bug/840697](https://bugs.launchpad.net/ubuntu/+source/prelink/+bug/840697)

---

### Post by tempusfuoit on 2012-03-06
I've gotten 3 different computers to run prelink by doing the following:

sudo gedit /etc/prelink.conf

then paste the following and save:

-b /usr/lib/klibc/bin
-b /usr/lib/libreoffice/basis3.4/program
-b /usr/lib/libreoffice/program
-b /usr/lib/ure/bin
-b /usr/bin/aptitude-curses

If you use Skype also add this or else prelink will break Skype.

-b /usr/bin/skype

---

### Post by sppo71 on 2012-03-09
> **tempusfuoit said:**
> I've gotten 3 different computers to run prelink by doing the following:

sudo gedit /etc/prelink.conf

then paste the following and save:

-b /usr/lib/klibc/bin
-b /usr/lib/libreoffice/basis3.4/program
-b /usr/lib/libreoffice/program
-b /usr/lib/ure/bin
-b /usr/bin/aptitude-curses

If you use Skype also add this or else prelink will break Skype.

-b /usr/bin/skype

Thank you very much. Prelink enabled instruction command to the end :D

---

