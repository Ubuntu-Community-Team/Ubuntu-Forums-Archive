---
title: "differences between debian and ubuntu (ubuntu core)"
date: 2012-08-21
forum: General Help
---

### Post by warren3000 on 2012-08-21
Hi 

I have a embeded device that is using u-boot to boot a kernel 2.6.38 compiled from source. The kernel is stored on nand flash memory. The rootfs sits on a sd card. Kernel compiled from source. So the kernel boots from flash and then mounts the sdcard, and starts using the fs it finds there. The device uses an arm processor.

Now if I use a romfs created from debian squeeze all works as expected. The kernel boots, mounts and starts running the rootfs.

But if I use an ubuntu rootfs (using ubuntu-core-11.10-core-armel.tar.gz) I get 
>> request_module: runaway loop modprobe binfmt-464c 
just after the fs is mounted. Googling this error says something about the files on the fs being the wrong type for the processor but the 'file' command says, for /bin/bash

bash: ELF 32-bit LSB executable, ARM, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.16, stripped (ubuntu)
bash: ELF 32-bit LSB executable, ARM, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, stripped (debian)

Now I know the the kernel version can not be that significant. Or can it? I have often upgraded a kernel from source without changing each and every executable on a system, so I'm guessing not. Otherwise the files are the same format. Besides I'm using 2.6.38 kernel match neither and the debian works fine.

But for /sbin/init 'file' command gives a very strange output for ubuntu:

init: ELF 32-bit LSB shared object, ARM, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.16, stripped (ubuntu)
init: ELF 32-bit LSB executable, ARM, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, stripped (debian)

Im not sure how significant this can be, that the debian init is a executable and the ubuntu is a shared object? Why is init a shared object on ubuntu? 

Or perhaps the problem is much simpler. Could the issue be the wrong kernel boot parameter, im using:
root=/dev/mmcblk0p1 noinitrd console=ttySAC0,115200 init=/sbin/init

Perhaps ubuntu puts things in a different place and I need to tell the kernel where to look.
Then again I could be on the wrong track altogether.

Any help is GREATLY appreciated.

Regards

---

### Post by lykwydchykyn on 2012-08-21
I don't know the answer for sure, but /sbin/init is part of the upstart package on Ubuntu, which is a totally different init system from what debian uses (sysv-init).  They're not the same piece of software, even though they're both called "init".

---

### Post by warren3000 on 2012-08-23
For those that find this:

ubuntu core supports armv7, I'm using an armv6

It would help if 'file' command could also show this.

---

