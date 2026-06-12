---
title: "Sudo make error 2"
date: 2011-05-01
forum: General Help
---

### Post by EzraBynx on 2011-05-01
Hello,

I just downloaded and installed the new Ubuntu 11.04.  After trying to install my raid driver I get the following error.


make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /raiddrivers/rr232x-linux-src-v1.10/product/rr232x/linux/.build/os_linux.o
In file included from /raiddrivers/rr232x-linux-src-v1.10/product/rr232x/linux/.build/os_linux.c:6:0:
/raiddrivers/rr232x-linux-src-v1.10/osm/linux/osm_linux.h:12:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[2]: *** [/raiddrivers/rr232x-linux-src-v1.10/product/rr232x/linux/.build/os_linux.o] Error 1
make[1]: *** [_module_/raiddrivers/rr232x-linux-src-v1.10/product/rr232x/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [rr232x.ko] Error 2

Prior ubuntu versions this did work.  I am using sudo make. Any help would be appreciated.

---

### Post by clifforddc on 2011-05-03
I am having same issue attempting to compile Rr2332x driver - reverting to older kernel as work-around. the issue is the driver has to be included in a new initrd for the RAID card to work on boot

Dave

I believe issue is related to a new file or structure.

---

### Post by clifforddc on 2011-05-10
I found a solution patch to correct the rr232x source structure to compile correctly, install and work in 2.6.38 kernel. 

Thanks to Nagilum's Cookie Jar 

[http://cakebox.homeunix.net/wordpress/?p=190&cpage=1#comment-4221](http://cakebox.homeunix.net/wordpress/?p=190&cpage=1#comment-4221)

Life is now better........................

---

### Post by Akalanka on 2011-05-11
I got same kind of error when i was trying to install mitm-ssh
-- 
netfilter.h: In function ‘get_real_target’:
netfilter.h:8:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make: *** [mitm-ssh.o] Error 1
--

Finally, I could solved the problem as follows

-- Opened the file "netfilter.h" which error contains
--Commented the line contains " #include <linux/config.h> "
//#include <linux/config.h>

Then i used "make" and "make install" .. It  worked perfect

I think Ubuntu 11.04 does not require to include as an external source file.
Just try it.

----------------------------------
[www.akalanka.net]("http://www.akalanka.net")

---

### Post by clifforddc on 2011-05-11
> **Akalanka said:**
> I got same kind of error when i was trying to install mitm-ssh
-- 
netfilter.h: In function ‘get_real_target’:
netfilter.h:8:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make: *** [mitm-ssh.o] Error 1
--

Finally, I could solved the problem as follows

-- Opened the file "netfilter.h" which error contains
--Commented the line contains " #include <linux/config.h> "
//#include <linux/config.h>

Then i used "make" and "make install" .. It  worked perfect

I think Ubuntu 11.04 does not require to include as an external source file.
Just try it.

----------------------------------
[www.akalanka.net]("http://www.akalanka.net")

A small addition - 

the header file [B]config.h 
[/B]was removed sometime after the 2.6.35-28 kernel (this version worked for me to compile the rr2323x driver. 

The other changes are needed to support the changed structures in the linux 2.6.38 kernel

---

### Post by AllGamer on 2011-07-06
i'm having the exact same problem with **rr26xx** and **rr174x** on several servers.

can some one please post the lines in **osm_linux.h** that were patched/modified to be 2.6.38.x compatible?

if i comment out this section, then i get another error
```

/* 
#ifndef AUTOCONF_INCLUDED
#include <linux/config.h> 
#endif
*/

```

some people says that it worked for them, but it did not in my case, any help would be appreciated

thanks

---

