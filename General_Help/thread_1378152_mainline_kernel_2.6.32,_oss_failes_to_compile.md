---
title: "mainline kernel 2.6.32, oss failes to compile"
date: 2010-01-11
forum: General Help
---

### Post by monkman on 2010-01-11
ubuntu 9.10 (64bit)
i've installed:
```
http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/linux-headers-2.6.32-02063203_2.6.32-02063203_all.deb
```

```
http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/linux-image-2.6.32-02063203-generic_2.6.32-02063203_amd64.deb
```

```
http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/linux-source-2.6.32_2.6.32-02063203_all.deb
```

then i linked:

```
ls -l
insgesamt 20
drwxr-xr-x 23 root root 4096 2009-10-27 19:16 linux-headers-2.6.31-14
drwxr-xr-x  7 root root 4096 2009-10-27 19:16 linux-headers-2.6.31-14-generic
drwxr-xr-x 23 root root 4096 2010-01-10 11:26 linux-headers-2.6.31-17
drwxr-xr-x  7 root root 4096 2010-01-10 11:26 linux-headers-2.6.31-17-generic
drwxr-xr-x 23 root root 4096 2010-01-11 10:29 linux-headers-2.6.32-02063203
lrwxrwxrwx  1 root src    29 2010-01-11 10:37 linux-headers-2.6.32-02063203-generic -> linux-headers-2.6.32-02063203

```

unfortunalety this doesn't seem to be enough. what can i do here?

```
sudo dpkg -i oss-linux-4.2-2002_amd64.deb 
[sudo] password for monkman: 
(Lese Datenbank ... 167013 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von oss-linux 4.2-2002 (durch oss-linux-4.2-2002_amd64.deb) ...
OSS not loaded.
Entpacke Ersatz für oss-linux ...
Upgrading OSS - will not purge /usr/lib/oss.
Richte oss-linux ein (4.2-2002) ...
Building OSS Modules for Linux-unknown 2.6.32-02063203-generic

OSS build environment set up for REGPARM kernels


Warning: Cannot locate the Linux kernel development package for
         Linux kernel version  2.6.32-02063203-generic
         Please install the kernel development package if linking the
         OSS modules fails.

The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. Please refer
to the documentation of your Linux distribution if there are any
difficulties in installing the kernel/driver development environment.

For your Linux distribution the right kernel source package
might be kernel-source.

Under Ubuntu you may need to prepare the kernel environment
after downloading the kernel sources using

  sudo apt-get install linux-headers-2.6.32-02063203-generic
  cd /usr/src/linux-headers-2.6.32-02063203-generic/

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.32-02063203-generic/build M=/usr/lib/oss/build modules
make: *** /lib/modules/2.6.32-02063203-generic/build: No such file or directory.  Schluss.
make: *** [default] Fehler 2
Forcing re-detection of installed soundcards
Starting Open Sound System
Relinking OSS kernel modules for "2.6.32-02063203-generic SMP mod_unload modversions "
This may take few moments - please stand by...

OSS build environment set up for REGPARM kernels


Warning: Cannot locate the Linux kernel development package for
         Linux kernel version  2.6.32-02063203-generic
         Please install the kernel development package if linking the
         OSS modules fails.

The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. Please refer
to the documentation of your Linux distribution if there are any
difficulties in installing the kernel/driver development environment.

For your Linux distribution the right kernel source package
might be kernel-source.

Under Ubuntu you may need to prepare the kernel environment
after downloading the kernel sources using

  sudo apt-get install linux-headers-2.6.32-02063203-generic
  cd /usr/src/linux-headers-2.6.32-02063203-generic/

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.32-02063203-generic/build M=/usr/lib/oss/build modules
make: *** /lib/modules/2.6.32-02063203-generic/build: No such file or directory.  Schluss.
make: *** [default] Fehler 2

Relinking the OSS kernel modules failed

Verarbeite Trigger für libc-bin ...
ldconfig deferred processing now taking place
Verarbeite Trigger für man-db ...

```

thank you!

---

