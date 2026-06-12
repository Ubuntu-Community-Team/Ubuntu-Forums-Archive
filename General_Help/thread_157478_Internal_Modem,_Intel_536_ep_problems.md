---
title: "Internal Modem, Intel 536 ep problems"
date: 2006-04-09
forum: General Help
---

### Post by david.holland on 2006-04-09
[B]I have managed to install the driver/loadable module for an internal modem; chipset Intel 536ep, in Fedora Core 3; but I am experiencing major problems getting this to install in Ubuntu 5.10.

Logged in as root, the contents of /root/Intel-536/ are below:[/B]

root@ubuntu:~/Intel-536# ls -la
total 76
drwxr-xr-x   3 root root  4096 2005-08-04 18:47 .
drwxr-xr-x  22 root root  4096 2006-04-09 15:05 ..
-rwxr-xr--   1 root root  4252 2005-07-26 16:59 config_check
drwxr-xr-x   3 root root  4096 2005-08-04 18:47 coredrv
-rwxr-xr-x   1 root root 15639 2005-07-26 16:59 hamregistry
-rwxr-xr--   1 root root  3467 2005-07-26 16:59 Intel536_boot
-rwxr-xr--   1 root root  8036 2005-07-26 16:59 Intel536_inst
-rw-r--r--   1 root root  1879 2005-07-26 16:59 license.txt
-rw-r--r--   1 root root  2487 2005-07-26 16:59 makefile
-rw-r--r--   1 root root 18242 2005-07-26 16:59 readme.txt
root@ubuntu:~/Intel-536#
-----------------------------------------------------------

**The read me says:**   
   1. login as ROOT 
   2. extract the archive into a directory with "tar -zxvf <archivename>.tgz"
   3. cd into the directory it created.
   4. Type: make clean
   5. Type: make 536
   6. Type: make install
-----------------------------------------------------------

**So I 'make clean':**

root@ubuntu:~/Intel-536# make clean
Try `uname --help' for more information.
cd coredrv; make clean
make[1]: Entering directory `/root/Intel-536/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/root/Intel-536/coredrv'
rm -f *.o *.ko
root@ubuntu:~/Intel-536#
-----------------------------------------------------------

**Then 'make 536', but this fails to build driver:**

root@ubuntu:~/Intel-536# make 536
Try `uname --help' for more information.
   Module precompile check
   Current running kernel is: 2.6.12-9-386
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
cd coredrv && make 536core_26 && \
cp Intel536.ko .. && cd .. && \
strip --strip-debug Intel536.ko && \
exit; \
ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
if [  ]; then \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
else \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
cp Intel536.o .. ; \
if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.12-9-386
make[1]: Entering directory `/root/Intel-536/coredrv'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/root/Intel-536/coredrv modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /root/Intel-536/coredrv/coredrv.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/root/Intel-536/coredrv/coredrv.o] Error 127
make[2]: *** [_module_/root/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/root/Intel-536/coredrv'
2.6.12-9-386
Failed to build driver
root@ubuntu:~/Intel-536#
----------------------------------------------------------

**As as a result, 'make install' fails too:**
root@ubuntu:~/Intel-536# make install
Try `uname --help' for more information.
rm -f /etc/hamregistry.bin
bash Intel536_inst
running kernel 2.6.12-9-386
installing hamregistry, used for persistant storage
installing Intel536 driver
install: cannot stat `Intel536.ko': No such file or directory
make: *** [install] Error 1
root@ubuntu:~/Intel-536#
---------------------------------------------------------------


I would be grateful if someone can advise:
a) how I can get this piece of hardware working in Ubuntu 5.10; as I have had this working in Fedora Core 3
b) If any other software/packages are required then these will need to be downloaded via Windows XP, is this possible; as I have no internet connection via Ubuntu - so don't bother with the usual answer of "in terminal you need to do: sudo apt-get install linux-source-your kernel version".  As I say NO INTERNET CONNECTION!
c) if an internet connection is required in Ubuntu 5.10 to get dependencies to install modem drivers where can you give feedback to developers as I need an internet connection to GET dependencies.

My machine is a Pentium 3 1.0GHz/256MB RAM/20GB Hdd, dual booted with Ubuntu 5.10 and Windows XP Home.

Many thanks in Advance

---

### Post by fatdaddy on 2006-04-09
As a thought for a couple of things to check.

Make sure your driver works on a 386 kernal which you appear to be running.

Your printout seems to error when dealing with gcc 3.4 so you would want to make sure that item is installed on your computer

---

