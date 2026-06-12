---
title: "how to install driver"
date: 2011-10-27
forum: General Help
---

### Post by atif7865 on 2011-10-27
I have a network card that i need to update the driver for. i Have got the drivers from the venders website(its a broadcom) but i dont know how to install those drivers on the machine.

the following are the list of files inside the driver folder.

1- Changelog
2-tg3-3.116j.tar.gz
3-tg3-3.116j-1.src.rpm
4-readme.txt

how do i go about installing this driver for my network card guys?

Thanks

---

### Post by enkay009 on 2011-10-27
Okay it looks like the vendor gave you the source code for the drivers. Before you start anything have a look at the readme file. Usually all the installation instructions and compilation instructions are in there.

And if not, untar tg3-3.116j.tar.gz...
```
tar xzf tg3-3.116j.tar.gz
```

And look for either a README, or INSTALL file in there.

---

### Post by atif7865 on 2011-10-27
thanks for the reply,

i tar the file and got the instruction. as i was following it on the make command i got this error, what does this mean?


sudo make
gcc -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -I/lib/modules/3.0.0-12-generic/build/include -fno-strict-aliasing -DOLD_NETIF -mno-red-zone -mcmodel=kernel -pipe -finline-limit=2000 -O2   -c -o tg3.o tg3.c
In file included from /lib/modules/3.0.0-12-generic/build/include/linux/kernel.h:13:0,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/cache.h:4,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/time.h:7,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/stat.h:60,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/module.h:10,
                 from tg3.c:32:
/lib/modules/3.0.0-12-generic/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [tg3.o] Error 1

---

### Post by atif7865 on 2011-10-27
i get this error when i try to install source RPM



sudo rpmbuild -bb tg3.spec 
Executing(%prep): /bin/sh -e /var/tmp/rpm-tmp.qNKBnd
+ umask 022
+ cd /home/atef/rpmbuild/BUILD
+ cd /home/atef/rpmbuild/BUILD
+ rm -rf tg3-3.116j
+ /bin/bzip2 -dc /home/atef/rpmbuild/SOURCES/tg3-3.116j.tar.bz2
+ /bin/tar -xvvf -
drwxr-xr-x mcarlson/305      0 2011-01-21 13:50 tg3-3.116j/
-rwxr--r-- mcarlson/305   7837 2011-01-04 15:28 tg3-3.116j/makeflags.sh
-rw-r--r-- mcarlson/305 399554 2010-12-09 19:38 tg3-3.116j/ChangeLog
-rw-r--r-- mcarlson/305   3888 2011-01-04 15:27 tg3-3.116j/Makefile
-rw-r--r-- mcarlson/305  43934 2011-01-04 15:30 tg3-3.116j/tg3_firmware.h
-rw-r--r-- mcarlson/305 445295 2011-01-21 13:50 tg3-3.116j/tg3.c
-rw-r--r-- mcarlson/305 119912 2011-01-06 21:41 tg3-3.116j/tg3.h
-rw-r--r-- mcarlson/305  24624 2011-01-11 21:04 tg3-3.116j/tg3_vmware.c
-rw-r--r-- mcarlson/305  37228 2011-01-04 15:29 tg3-3.116j/tg3_compat.h
-rw-r--r-- mcarlson/305  15153 2010-11-12 15:40 tg3-3.116j/LICENSE
-rw-r--r-- mcarlson/305   2246 2011-01-04 15:29 tg3-3.116j/tg3_compat2.h
-rw-r--r-- mcarlson/305   3445 2011-01-04 15:29 tg3-3.116j/tg3.4
-rw-r--r-- mcarlson/305   2155 2011-01-13 13:44 tg3-3.116j/tg3_vmware.h
-rw-r--r-- mcarlson/305  11410 2011-01-21 13:50 tg3-3.116j/README.TXT
-rw------- mcarlson/305   2437 2011-01-04 15:28 tg3-3.116j/esx_ioctl.h
+ STATUS=0
+ [ 0 -ne 0 ]
+ cd tg3-3.116j
+ exit 0
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.i0cvBe
+ umask 022
+ cd /home/atef/rpmbuild/BUILD
+ cd tg3-3.116j
+ value=
+ [ -z  ]
+ uname -r
+ KVER=3.0.0-12-generic
+ make KVER=3.0.0-12-generic
sh makeflags.sh /lib/modules/3.0.0-12-generic/build  > tg3_flags.h
gcc -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -I/lib/modules/3.0.0-12-generic/build/include -fno-strict-aliasing -DOLD_NETIF -mno-red-zone -mcmodel=kernel -pipe -finline-limit=2000 -O2   -c -o tg3.o tg3.c
In file included from /lib/modules/3.0.0-12-generic/build/include/linux/kernel.h:13:0,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/cache.h:4,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/time.h:7,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/stat.h:60,
                 from /lib/modules/3.0.0-12-generic/build/include/linux/module.h:10,
                 from tg3.c:32:
/lib/modules/3.0.0-12-generic/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [tg3.o] Error 1
error: Bad exit status from /var/tmp/rpm-tmp.i0cvBe (%build)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.i0cvBe (%build)



any clues??

---

### Post by enkay009 on 2011-10-27
It means you're missing the header file linkage.h. These are usually inside devel flavored packages.

Start with the documentation (README) and check if they mention any prerequisites. Ubuntu is a fairly popular Linux distribution so it's possible that they'll list the exact packages. 

If not... install this utility...

```
sudo apt-get install apt-file
```

It helps you looks for packages by the files it contains. After it's been installed (and configured... automatically configured nothing to sweat over)... you can check if any packages contain linkage.h by running...

```
apt-file search linkage.h
```

---

### Post by enkay009 on 2011-10-27
> **atif7865 said:**
> i get this error when i try to install source RPM

You don't need to install the source RPM. You already have the source. You'll just need to resolve the dependency issue. Try the steps I mentioned earlier (a few minutes ago).

---

### Post by atif7865 on 2011-10-27
> **enkay009 said:**
> It means you're missing the header file linkage.h. These are usually inside devel flavored packages.

Start with the documentation (README) and check if they mention any prerequisites. Ubuntu is a fairly popular Linux distribution so it's possible that they'll list the exact packages. 

If not... install this utility...

```
sudo apt-get install apt-file
```

It helps you looks for packages by the files it contains. After it's been installed (and configured... automatically configured nothing to sweat over)... you can check if any packages contain linkage.h by running...

```
apt-file search linkage.h
```

i did install the utility and run it but i get the following error:

E: The cache is empty. You need to run 'apt-file update' first.

i ran the apt-file update too but still same error

---

### Post by atif7865 on 2011-10-27
i think i should tell you guys that i am trying to install this driver because i believe this will help me to use jumbo frames on it.
i have started another thread in networking section but no replies so far.

I am trying to set up a lab in my home. for that i need to have a mtu value of atleast 1546,
I have a broadcom gigabit NIC BCM5751KFBG PCI Express,but i cant increase the mtu on my machine.
I have a hp pavillion desktop running ubuntu 11.10.

I also have pci boradcom NIC BCM5782KFB but i still cant change mtu value. Documents from broadcom indicate that the card is capable of jumbo frames upto 9K.([http://www.broadcom.com/docs/support...me_DTM_306.pdf](http://www.broadcom.com/docs/support...me_DTM_306.pdf))

I try to change the value but issuing followig command:

"sudo ifconfig eth1 mtu 1600"
and i get the following error:
SIOCSIFMTU: invalid argument

I cant even change it to 1501,

---

### Post by enkay009 on 2011-10-27
> **atif7865 said:**
> i did install the utility and run it but i get the following error:

E: The cache is empty. You need to run 'apt-file update' first.

i ran the apt-file update too but still same error

Weird. Not sure why "apt-file update" didn't work for you. 

To summarize the problem with compile is that it's looking for a header file that it can't find. Which means you need to figure out which package contains it.

Normally this utility (apt-file) can help, but since it doesn't work, all I can unfortunately suggest are google searches to determine which Ubuntu package contains this file.

I would search something like "linkage.h ubuntu"

After you fix this it's possible that you'll run into another missing header problem, so you'll probably need to rinse and repeat.

And if you can't find the package, you can always look for the source and compile any ".so" you need.

---

### Post by atif7865 on 2011-10-27
> **enkay009 said:**
> Weird. Not sure why "apt-file update" didn't work for you. 

To summarize the problem with compile is that it's looking for a header file that it can't find. Which means you need to figure out which package contains it.

Normally this utility (apt-file) can help, but since it doesn't work, all I can unfortunately suggest are google searches to determine which Ubuntu package contains this file.

I would search something like "linkage.h ubuntu"

After you fix this it's possible that you'll run into another missing header problem, so you'll probably need to rinse and repeat.

And if you can't find the package, you can always look for the source and compile any ".so" you need.

Thanks for the reply, i run a find / -name linkage.h and got many results back. 
given the error message that i got, what should i do now ? do i have to copy this linkage.h anywhere ?

---

### Post by enkay009 on 2011-10-27
Okay so the point of that command was to determine which package contains required header file. Since you've got many matches back, I'm gonna guess it's because there's different versions of it available.

So go back to the documentation and check which version of the package/library is compatible with the drivers. If none is explicitly mentioned, then use the package that doesn't have a version in the name.

With the package picked out, you just need to install it.

```
sudo apt-get install packagename
```

And substitute packagename with the package that contains linkage.h

---

### Post by grumio8 on 2011-11-01
I am having the same issue with the same Broadcom driver. I am running 11.10 server. 
The file linkage.h exists, the error is happening at line 5 of the file:
```
#include asm/linkage.h
```
 Am I missing some sort of development header package? or what? Any help would be appreciated.

---

### Post by enkay009 on 2011-11-01
I don't have much experience with this driver but I do have some experience with compilers. I can try to help you figure out what the error message means.

Can you post the exact error you're getting?

---

### Post by grumio8 on 2011-11-01
Here is the response I get when I run make:
```
~/Server/Linux/Driver/tg3-3.116j$ make
gcc -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -I/lib/modules/3.0.0-12-generic-pae/build/include -fno-strict-aliasing -DOLD_NETIF -O2   -c -o tg3.o tg3.c
In file included from /lib/modules/3.0.0-12-generic-pae/build/include/linux/kernel.h:13:0,
                 from /lib/modules/3.0.0-12-generic-pae/build/include/linux/cache.h:4,
                 from /lib/modules/3.0.0-12-generic-pae/build/include/linux/time.h:7,
                 from /lib/modules/3.0.0-12-generic-pae/build/include/linux/stat.h:60,
                 from /lib/modules/3.0.0-12-generic-pae/build/include/linux/module.h:10,
                 from tg3.c:32:
/lib/modules/3.0.0-12-generic-pae/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [tg3.o] Error 1

```
Thanks for the potential help

---

### Post by grumio8 on 2011-11-02
Here are the first couple lines of the file that is erroring out:
```
:~$ more /lib/modules/3.0.0-12-generic-pae/build/include/linux/linkage.h 
``````

#ifndef _LINUX_LINKAGE_H
#define _LINUX_LINKAGE_H

#include <linux/compiler.h>
#include <asm/linkage.h>

#ifdef __cplusplus
#define CPP_ASMLINKAGE extern "C"
#else
#define CPP_ASMLINKAGE
#endif

#ifndef asmlinkage
#define asmlinkage CPP_ASMLINKAGE
#endif

#define __page_aligned_data     __section(.data..page_aligned) __aligned(PAGE_SI
ZE)
#define __page_aligned_bss      __section(.bss..page_aligned) __aligned(PAGE_SIZ
E)

/*
 * For assembly routines.
--More--(20%)

```You can see from the make error that the 5th line is the issue:
```
#include <asm/linkage.h>
```I don't know anything about header files but it seems odd to me that the file linkage.h would call another file called linkage.h inside itself.

---

### Post by enkay009 on 2011-11-02
It's not that unusual for a header to call another header. 

I suspect that you don't have **asm/linkage.h** in one of your include directories. Can you check on your machine?

---

### Post by grumio8 on 2011-11-02
would that be in /usr/include ? because in usr/include i have no asm directory, only asm-generic. There is no linkage.h file in the asm-generic directory.

---

### Post by enkay009 on 2011-11-03
That would be the problem. Now why there isn't an asm directory is another story.

I checked my machine and it looks like I have an asm directory but it's a broken symlink to asm-x86.

And then I found this: [https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/576558](https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/576558) An old bug report about just this. 

Since the Ubuntu maintainers didn't fix it (considering it's seemingly an easy fix), I'm guessing they had good reasons.

In that bug report someone posts a link to a blog where they try to "fix" the issue. His post suggests editing the header. Don't. Leave it unchanged.

The easier fix is to simply create that missing asm-x86 symlink. But now I'm assuming a few things...

[LIST]
[*]you see the same thing I do (broken symlink)
[*]you're running Ubuntu on an x86 family processor
[/LIST]
I can't guarantee this will work or that your driver will be compiled correctly. So do this at your own risk. 

When you're done, be sure to remove that symlink you created.

---

