---
title: "captive aquire"
date: 2005-01-23
forum: General Help
---

### Post by MaTZ! on 2005-01-23
```
Captive ntfs is a great program that lets you read and write to ntfs(windows) partitons, but on ubuntu it kept freezing well until now...

   1. First download the rpm package from [http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)
   2. Install kernel-headers for your kernel revision
          * To find out your kernel type in the terminal 'uname -a'
          * To install kernel-headers use synaptic or apt-get to find and install the correct version
          * in my case i did 'apt-get install linux-headers-2.6.8.1-4-k7'
          * if do not know use 'apt-cache search linux-headers' for list of kernel headers available
   3. use alien to convert rpm to deb package
          * run 'alien captive-static-1.1.5-0.i386.rpm'
          * This creates captive-static_1.1.5_1.i386.deb
   4. Install deb package using 'dpkg -i captive-static_1.1.5_1.i386.deb'
   5. run 'captive-install-acquire'
          * Follow directions to find ntfs.sys and other files that captive needs.
   6. run '/usr/share/lufs/prepmod'
   7. create user and group named captive
   8. use 'mount -t captive-ntfs /dev/hd?? /mnt/winpart' to mount. Change options to enable write etc....
``` 

i followed this how-to (found in this forum)
when i "run '/usr/share/lufs/prepmod"...
```
:~ $ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-3-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-3-386/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.8.1-3-386/build
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
+ find /lib/modules/2.6.8.1-3-386/build -name .depend|xargs rm -f; rm -f /lib/modules/2.6.8.1-3-386/build/scripts/mkdep; rm -f /lib/modules/2.6.8.1-3-386/build/scripts/split-include; make -C /lib/modules/2.6.8.1-3-386/build dep
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
*** Warning: make dep is unnecessary now.
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-3-386.
Detected Linux kernel sources "/lib/modules/2.6.8.1-3-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-3-386/build
                /usr/src/kernel-headers-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-3-386
``` 

** gcc: command not found**  -> so i do 
```
:~ $ sudo apt-get install gcc-3.4
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
gcc-3.4 è già alla versione più recente.
0 aggiornati, 0 installati, 0 da rimuovere e 34 non aggiornati.
``` 

it says that gcc-3.4 is installed.
So i think that the problem is that i havent the kernel-sources.
my version is:
```
 uname -a
Linux MaTz 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux
``` 
i try atp-cache search but i don't found anything.

so plz help me :)

---

### Post by MaTZ! on 2005-01-23
subscrived

---

### Post by tricky1 on 2005-01-29
$ sudo apt-get install build-essential

---

