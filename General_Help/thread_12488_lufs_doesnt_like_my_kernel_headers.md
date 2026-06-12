---
title: "lufs doesnt like my kernel headers"
date: 2005-01-24
forum: General Help
---

### Post by Razvan on 2005-01-24
hi all,

i want to use captive, i have been lucky till it wants to prepare the lufs module, it says

```
root@razvan:/home/udssr # /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.10-2-k7 (base version 2.6.10)
Destination module directory: /lib/modules/2.6.10-2-k7/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.10-2-k7/build
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.10-2-k7/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
make: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.10-2-k7«
  CC [M]  /usr/share/lufs/2.6/dir.o
  CC [M]  /usr/share/lufs/2.6/file.o
  CC [M]  /usr/share/lufs/2.6/inode.o
  CC [M]  /usr/share/lufs/2.6/proc.o
  CC [M]  /usr/share/lufs/2.6/symlink.o
  LD [M]  /usr/share/lufs/2.6/lufs.o
  Building modules, stage 2.
  MODPOST
*** Warning: "kill_proc_info" [/usr/share/lufs/2.6/lufs.ko] undefined!
  CC      /usr/share/lufs/2.6/lufs.mod.o
  LD [M]  /usr/share/lufs/2.6/lufs.ko
make: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.10-2-k7«
+ /bin/rm -rf /lib/modules/2.6.10-2-k7/kernel/fs/lufs; /bin/mkdir -p /lib/modules/2.6.10-2-k7/kernel/fs/lufs; /bin/ln -s /var/lib/lufs/lufs.ko /lib/modules/2.6.10-2-k7/kernel/fs/lufs/lufs.ko
+ /sbin/rmmod lufs 2>/dev/null; /sbin/insmod /lib/modules/2.6.10-2-k7/kernel/fs/lufs/lufs.ko 2>/dev/null
Failed to prepare lufs.ko module for your Linux kernel 2.6.10-2-k7.
Detected Linux kernel sources "/lib/modules/2.6.10-2-k7/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-2-k7/build
                /usr/src/kernel-headers-2.6.10-2-k7
                /usr/src/linux-2.6.10-2-k7
                /usr/src/linux-2.6.10
                /usr/src/linux
                /usr/src/kernel-source-2.6.10-2-k7
root@razvan:/home/udssr #
```

i installed kernel v 2.6.10-2-k7, kernel headers are installed : 

linux-headers-2.6.10-2
linux-headers-2.6.10-2-386
linux-headers-2.6.10-2-k7

i found out that the /usr/src/linux-headers-2.6.10-2-k7 directory is mainly symlinks...is that an issue?

what do i have to do to get my lufs module installed? 

thanks, Martin

---

### Post by dave_blob on 2005-02-12
I have the exact same problem, except i am using the newer 2.6.10-3-k7 kernal.

Anyone have any ideas?

---

### Post by Gymnae on 2005-02-15
> **dave_blob]I have the exact same problem, except i am using the newer 2.6.10-3-k7 kernal.

Anyone have any ideas?[/QUOTE]

 I'm suffering from the exact same situation!

Here's my bash log:
[QUOTE]$ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.10-3-k7 (base version 2.6.10)
Destination module directory: /lib/modules/2.6.10-3-k7/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.10-3-k7/build
+ set -e said:**
>   /usr/share/lufs/2.6/dir.o
  CC [M]  /usr/share/lufs/2.6/file.o
  CC [M]  /usr/share/lufs/2.6/inode.o
  CC [M]  /usr/share/lufs/2.6/proc.o
  CC [M]  /usr/share/lufs/2.6/symlink.o
  LD [M]  /usr/share/lufs/2.6/lufs.o
  Building modules, stage 2.
  MODPOST
*** Warning: "kill_proc_info" [/usr/share/lufs/2.6/lufs.ko] undefined!
  CC      /usr/share/lufs/2.6/lufs.mod.o
  LD [M]  /usr/share/lufs/2.6/lufs.ko
make: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.10-3-k7«
+ /bin/rm -rf /lib/modules/2.6.10-3-k7/kernel/fs/lufs; /bin/mkdir -p /lib/module s/2.6.10-3-k7/kernel/fs/lufs; /bin/ln -s /var/lib/lufs/lufs.ko /lib/modules/2.6. 10-3-k7/kernel/fs/lufs/lufs.ko
+ /sbin/rmmod lufs 2>/dev/null; /sbin/insmod /lib/modules/2.6.10-3-k7/kernel/fs/ lufs/lufs.ko 2>/dev/null
Failed to prepare lufs.ko module for your Linux kernel 2.6.10-3-k7.
Detected Linux kernel sources "/lib/modules/2.6.10-3-k7/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-3-k7/build
                /usr/src/kernel-headers-2.6.10-3-k7
                /usr/src/linux-2.6.10-3-k7
                /usr/src/linux-2.6.10
                /usr/src/linux
                /usr/src/kernel-source-2.6.10-3-k7


I really would like to get captive running! 
Then it would maybe be possible to play already on the ntfs-partitions installed games with cedega

---

### Post by joobuntjoo on 2005-02-21
Just thought I'd add this in case anyone does a search. I had the same problem today and used these forums for ideas. Managed to fix it by doing the following...

apt-get install linux-kernel-source.x.x.x (not sure if this was necessary, but mentioning in case)
apt-get install linux-kernel-headers.x.x.x

I still had the problem at this point, but main thing that did seem to get it working was an apt-get install gcc. Once I had done this 
/usr/share/lufs/prepmod worked fine, then was able to mount using captive-ntfs.

Ian

---

### Post by sas on 2005-02-22
Hi, I've ran up against a problem when trying to install Captive NTFS. 

```
dean@bacardi:~ $ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-3-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-3-386/kernel/fs/lufs
Failed to find kernel headers for 2.6.8.1-3-386
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-3-386.
No Linux kernel sources for your running kernel were found.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-3-386/build
                /usr/src/kernel-headers-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-3-386
``` 

It says I haven't got the kernel headers installed, I've installed all the kernel headers that could possibly  be my machine - all versions that are 386 or 686. However none of them match my exact version number, which cannot be found. 

```
dean@bacardi:~ $ sudo apt-get install linux-kernel-source-2.6.8.1-3-386
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package linux-kernel-source-2.6.8.1-3-386
``` 

I've also tried running the command with just the dotted version number bits with no success. I'm currently running Hoary and gcc is installed.

---

### Post by byen on 2005-09-09
oops. wrong post.

---

### Post by cowlip on 2005-09-20
This is interesting, there doesn't seem to be a solution on Google either.  I have hte same problem with compiling spca5xx drivers as well as this captive ntfs error.

---

### Post by LaLLi on 2005-10-05
I found this solution on a nother forum...worked for me.
[http://www.linuxquestions.org/questions/showthread.php?s=&postid=1871011#post1871011](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1871011#post1871011)

sudo gedit /usr/share/lufs/2.6/inode.c
Search for:
/* notify the daemon that we're going bye-bye */
and then change "kill_proc_info" to just "kill_proc" and its good.

Why it works can is on that original post.

---

### Post by cowlip on 2005-10-09
[QUOTE=LaLLi]I found this solution on a nother forum...worked for me.
[http://www.linuxquestions.org/questions/showthread.php?s=&postid=1871011#post1871011](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1871011#post1871011)

sudo gedit /usr/share/lufs/2.6/inode.c
Search for:
/* notify the daemon that we're going bye-bye */
and then change "kill_proc_info" to just "kill_proc" and its good.

Why it works can is on that original post.[/QUOTE]
Hehe :D

---

