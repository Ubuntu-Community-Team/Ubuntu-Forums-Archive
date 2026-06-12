---
title: "Error while trying to compile driver"
date: 2010-05-16
forum: General Help
---

### Post by damiensmith212 on 2010-05-16
Hi there,

I'm a recent Windows convert and have been trying unsuccessfully to compile and install a wireless driver. I don't think the compiling problem is limited to this driver though.

When trying to run 'make' on the driver source I'm getting the following response:

```
damien@Laptop:~/Downloads/rt2570-k2wrlz-1.6.4/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
rt2570.ko failed to build!
make: *** [module] Error 1
damien@Laptop:~/Downloads/rt2570-k2wrlz-1.6.4/Module$ 

```I also tried compiling another package; in this case Aircrack and get the following:

```
damien@Laptop:~/Downloads/aircrack-ng-1.1$ make
make -C src all
make[1]: Entering directory `/home/damien/Downloads/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/damien/Downloads/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/damien/Downloads/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/damien/Downloads/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/damien/Downloads/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:140: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:140: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3934: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/damien/Downloads/aircrack-ng-1.1/src'
make: *** [all] Error 2

```I have no idea if the problems are connected though. I've installed 'build-essential' but I can't figure out where I'm going  wrong. Any ideas?

---

### Post by mike555 on 2010-05-16
I think you need "sudo" in front of make...

---

### Post by DanCar on 2010-05-16
If sudo doesn't work try building with make V=2 and post more context.

---

### Post by WorMzy on 2010-05-16
> **mike555 said:**
> I think you need "sudo" in front of make...

He shouldn't, he's running 'make' in his own userspace. 'make install' needs sudo, as it needs write privileges in root-owned folders.

Damien, did you run ./configure before make? It will tell you if you have unmet dependencies, which is what I think the problem is in both cases.

---

### Post by trustno1. on 2010-05-16
why don't you just install it from repositories

[PHP]sudo apt-get install aircrack-ng[/PHP]

---

### Post by damiensmith212 on 2010-05-16
Thanks for replying guys.

> **DanCar said:**
> If sudo doesn't work try building with make V=2  and post more context.

Here you go.

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 0 modules - due to target is PHONY
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

```> **trustno1. said:**
> why don't you just install it from repositories
[PHP]sudo apt-get install aircrack-ng[/PHP]

I did in the end. I just ran that to see if it errored out too. Just looking for a common cause. 

> **WorMzy said:**
> 
Damien, did you run ./configure before make? It will tell you if you  have unmet dependencies, which is what I think the problem is in both  cases.

```
damien@Laptop:~/Downloads/rt2570-k2wrlz-1.6.4/Module$ ./configure
bash: ./configure: No such file or directory
damien@Laptop:~/Downloads/rt2570-k2wrlz-1.6.4/Module$
```No joy there either...

---

### Post by WorMzy on 2010-05-16
That's okay, not all source code packages come with a configure file. Check for a readme or install.txt and see if that lists what packages are required for compilation.

---

### Post by damiensmith212 on 2010-05-16
> **WorMzy said:**
> That's okay, not all source code packages come with a configure file. Check for a readme or install.txt and see if that lists what packages are required for compilation.

It doesn/t really list anything. I've included the text from the readme in case I've missed something obvious.

```
Installation instructions for the rt2570 Module

======================================================================
Build Instructions:
====================
For 2.4 or 2.6 series kernel:

        a. $tar -xvzf rt2570-x.x.x.tar.gz
        go to "./rt2570-x.x.x/Module" directory.

        b. $make # compile driver source code

        c. $make install # (as root) installs kernel module driver

_________
NOTES:

* Driver alias

        "make install" places the alias for the rt2570 driver in
        /etc/modules.conf (2.4 kernels) or /etc/modprobe.d/ralink
        (2.6 kernels).


======================================================================
INVOCATION
====================
Load the driver:

        $modprobe rt2570 [ifname=<name>] [debug=<mask>]

        <name> is the name of the device and defaults to "rausb%d".
        If more than one adapter is installed, specify <name> in
        sprintf format (e.g. "wlan%d" - without the quotes).
        Successive devices will then be named rausb0, rausb1, etc., or
        (using the example) wlan0, wlan1, etc. If there are already
        wired ethernet devices named eth0 and eth1, then specifying
        <name> as "eth%d" gives the adapter the name "eth2".

        <mask> is a decimal or hex number. See TESTING file. Ignored
        if driver compiled without debug support.

Start it up:

        $ifup rausb0        # If using Debian

======================================================================
UTILITY
====================
Rutilt provides a GUI- based driver configuration facility.

======================================================================
CONFIGURATION:
====================
The RT2570 driver can be configured via following interfaces,
i.e. (i)"iwconfig" command, (ii)"iwpriv" command

        i) iwconfig comes with kernel.
        ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for
            details.

======================================================================
MORE INFORMATION
====================
If you want rt2570 driver to auto-load at boot time:

A) choose rausb0 for first RT2570 WLAN card, rausb1 for second
   RT2570 WLAN card, etc.

B) create(edit) 'ifcfg-rausb0' file in /etc/sysconfig/network-scripts/
   edit (or add the line) in /etc/modules.conf:
        alias rausb0 rt2570

C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-rausb0
        DEVICE='rausb0'
        ONBOOT='yes'

        NOTE:
        if you use dhcp, add this line too .
        BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, add the line
        GATEWAY=x.x.x.x

    in /etc/sysconfig/network
```

---

### Post by Oblivion_4 on 2010-05-16
Why do I get the feeling that no one in this thread has done any programming in their entire lives? Oh here's why

crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory

These four lines tell you exactly whats going wrong. When aircrack-ng is compiling its looking for a library called openssl. Its not finding the library for one of two reasons. Either you don't have openssl installed(unlikely) or the compiler is looking in the wrong place for the openssl library.

Let's start with the first option. Run these commands in the directory you're compiling aircrack-ng. ALSO MAKE SURE YOU HAVEN'T INSTALLED OPENSSL FROM SOURCE BEFORE YOU RUN THIS COMMAND OR IT MAY CAUSE PROBLEMS IN THE FUTURE.

sudo apt-get install openssl
make

If that doesn't work, you're going to need to post the output to the next command to this forum

locate openssl

---

### Post by damiensmith212 on 2010-05-16
> **Oblivion_4 said:**
> 

Let's start with the first option. Run these commands in the directory you're compiling aircrack-ng. ALSO MAKE SURE YOU HAVEN'T INSTALLED OPENSSL FROM SOURCE BEFORE YOU RUN THIS COMMAND OR IT MAY CAUSE PROBLEMS IN THE FUTURE.

sudo apt-get install openssl
make

If that doesn't work, you're going to need to post the output to the next command to this forum

locate openssl

Installing openssl fails because it's already installed. Locate openssl returns the following:

```
damien@Laptop:~/Downloads/rt2570-k2wrlz-1.6.4/Module$ locate openssl
/etc/bash_completion.d/openssl
/etc/ssl/openssl.cnf
/usr/bin/openssl
/usr/lib/libgnutls-openssl.so.26
/usr/lib/libgnutls-openssl.so.26.14.12
/usr/lib/ssl/openssl.cnf
/usr/lib32/libgnutls-openssl.so
/usr/lib32/libgnutls-openssl.so.26
/usr/lib32/libgnutls-openssl.so.26.14.12
/usr/share/doc/openssl
/usr/share/doc/python-openssl
/usr/share/doc/openssl/CHANGES.SSLeay.gz
/usr/share/doc/openssl/NEWS.gz
/usr/share/doc/openssl/README.Debian
/usr/share/doc/openssl/README.gz
/usr/share/doc/openssl/README.optimization
/usr/share/doc/openssl/changelog.Debian.gz
/usr/share/doc/openssl/changelog.gz
/usr/share/doc/openssl/copyright
/usr/share/doc/python-openssl/changelog.Debian.gz
/usr/share/doc/python-openssl/changelog.gz
/usr/share/doc/python-openssl/copyright
/usr/share/man/man1/openssl.1ssl.gz
/usr/share/python-support/python-openssl.public
/var/lib/dpkg/info/openssl.conffiles
/var/lib/dpkg/info/openssl.list
/var/lib/dpkg/info/openssl.md5sums
/var/lib/dpkg/info/openssl.postinst
/var/lib/dpkg/info/python-openssl.list
/var/lib/dpkg/info/python-openssl.md5sums
/var/lib/dpkg/info/python-openssl.postinst
/var/lib/dpkg/info/python-openssl.prerm

```

---

### Post by damiensmith212 on 2010-05-17
I'm still having no joy resolving this. Can anyone help?

---

### Post by DanCar on 2010-05-18
google for openssl and aircrack .  The first link gives you this: [http://www.aircrack-ng.org/doku.php?id=install_aircrack](http://www.aircrack-ng.org/doku.php?id=install_aircrack)

---

### Post by Yellow Pasque on 2010-05-18
When you get errors about missing headers or .h files, you probably just need to install the appropriate -dev package(s), libssl-dev in the case of aircrack.

Actually, if there's already a version of whatever you're trying to build in the repo, apt-get build-dep should get at least most of the -dev packages you need, e.g:
```
sudo apt-get build-dep aircrack-ng
```

As for the kernel module, check the source directory to see if there's a make/build log to tell you what went wrong.

---

### Post by thogor on 2010-05-25
I have the same problem with module for wusb54g/rt2570 compilation:

x@x-desktop:~/Desktop/rt2570-k2wrlz-1.6.4/Module$ make
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.32-22-generic'
rt2570.ko failed to build!
make: ** [module] Erro 1

---

### Post by raesene on 2010-06-13
Hi all, 

just to say I've just installed aircrack-ng on 10.04.  Got the error you mentioned originally, but doing  

sudo apt-get install libssl-dev

 sorted the problem

---

