---
title: "Where is autoconf.h ?"
date: 2009-08-13
forum: General Help
---

### Post by Sepero on 2009-08-13
I'm trying to compile a driver and it says it requires autoconf.h. I have the kernel headers installed. Is autoconf.h not used in kernels anymore?
/usr/src/linux-headers-2.6.28-14-generic/include/linux/autoconf.h

If it is still used, how do I acquire it?


```

root@EMONSTER:/usr/src# cd intel-536-537/

root@EMONSTER:/usr/src/intel-536-537# make clean
cd coredrv; make clean
make[1]: Entering directory `/usr/src/intel-536-537/coredrv'
rm -f *.ko .*.o.cmd *.mod.c .*.ko.cmd *.o *~ core Module.* modules.*
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/intel-536-537/coredrv'
rm -f *.o *.ko

root@EMONSTER:/usr/src/intel-536-537# make 536
cd coredrv; make clean
make[1]: Entering directory `/usr/src/intel-536-537/coredrv'
rm -f *.ko .*.o.cmd *.mod.c .*.ko.cmd *.o *~ core Module.* modules.*
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/intel-536-537/coredrv'
rm -f *.o *.ko
   Module precompile check
   Current running kernel is: 2.6.28-14-generic
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1

root@EMONSTER:/usr/src/intel-536-537# apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.28-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@EMONSTER:/usr/src/intel-536-537# find /usr/src/linux-headers-2.6.28-14-generic/ -iname "autoconf.h"

root@EMONSTER:/usr/src/intel-536-537# ls /usr/src/linux-headers-2.6.28-14-generic/include/linux/auto*
/usr/src/linux-headers-2.6.28-14-generic/include/linux/auto_dev-ioctl.h
/usr/src/linux-headers-2.6.28-14-generic/include/linux/auto_fs4.h
/usr/src/linux-headers-2.6.28-14-generic/include/linux/auto_fs.h

```

---

### Post by Sepero on 2009-08-14
After a package search, "autoconf.h" was included in the first Jaunty kernel headers (2.6.28-11-generic), but none after that:
[http://packages.ubuntu.com/search?searchon=contents&keywords=autoconf.h&mode=exactfilename&suite=jaunty&arch=i386](http://packages.ubuntu.com/search?searchon=contents&keywords=autoconf.h&mode=exactfilename&suite=jaunty&arch=i386)

Why is autoconf.h not included in later kernel headers?

---

### Post by kustomjs on 2009-08-15
I am having the same issue as you are but only on server side of it and also I am trying to do the same modem as you are:

```
xxx@faxserver:/home/xxx# cd /home/xxxx/intel-536EP-2.56.76.0
xxx@faxserver:/home/xxxx/intel-536EP-2.56.76.0# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/xxxxxintel-536EP-2.56.76.0/coredrv'
rm -f *.ko .*.o.cmd *.mod.c .*.ko.cmd *.o *~ core Module.* modules.*
rm -rf .tmp_versions
make[1]: Leaving directory `/home/xxxx/intel-536EP-2.56.76.0/coredrv'
rm -f *.o *.ko
xxxx@faxserver:/home/xxxx/intel-536EP-2.56.76.0# make 536
   Module precompile check
   Current running kernel is: 2.6.24-24-server
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
```

---

### Post by jocko on 2009-08-15
> **Sepero said:**
> After a package search, "autoconf.h" was included in the first Jaunty kernel headers (2.6.28-11-generic), but none after that:
[http://packages.ubuntu.com/search?searchon=contents&keywords=autoconf.h&mode=exactfilename&suite=jaunty&arch=i386](http://packages.ubuntu.com/search?searchon=contents&keywords=autoconf.h&mode=exactfilename&suite=jaunty&arch=i386)

Why is autoconf.h not included in later kernel headers?
It is still part of the kernel headers. I have that file in the headers for 2.6.28-9, -11, -13, -14 and -15 (on x86_64, but I would be surprised if it would be any different on i386).
[packages.ubuntu.com]("http://packages.ubuntu.com/jaunty/i386/linux-headers-2.6.28-14-generic/filelist") seems to be missing the file lists for the packages containing the newer linux-headers, which is why you can't find autoconf.h in any other jaunty packages.
But your ls output still seems to indicate that you don't have it... That's weird. Have you tried reinstalling the linux-headers package?

---

### Post by Sepero on 2009-08-15
jocko, you are right.


The site packages.ubuntu.com does not appear to be keeping up with the latest packages, and therefore it is reporting incomplete information.


By reinstalling the headers:
sudo apt-get install linux-headers-2.6.28-14-generic --reinstall

The file autoconf.h is now again present.

---

### Post by Sepero on 2009-08-15
kustomjs, you are using an older version of the driver. Get the latest version of the driver here:

[http://x9000.fr:8088/Intel/](http://x9000.fr:8088/Intel/)
[http://x9000.fr:8088/Intel/intel-536EP-537EP-2009_07_07.tar.bz2](http://x9000.fr:8088/Intel/intel-536EP-537EP-2009_07_07.tar.bz2)

---

### Post by ink_rus on 2012-01-12
Latest version in oneric gives:

~ # modprobe Intel536
FATAL: Error inserting Intel536 (/lib/modules/3.0.0-12-generic/kernel/drivers/char/Intel536.ko): Invalid module format

:(

---

### Post by oldos2er on 2012-01-12
Closed. Please start a new thread for your question or problem.

---

