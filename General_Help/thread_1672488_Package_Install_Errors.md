---
title: "Package Install Errors"
date: 2011-01-20
forum: General Help
---

### Post by Linux000 on 2011-01-20
Every time I try to use Ubuntu Software Center, Synaptic or apt-get to install a package, it seems to give an error(okay, USC stops the install and Synaptic crashes), apt-get gives the traceback```
The following packages will be upgraded:
  google-talkplugin
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
*** glibc detected *** apt-get: double free or corruption (!prev): 0x083e0188 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0xb21501]
/lib/libc.so.6(+0x6dd70)[0xb22d70]
/lib/libc.so.6(cfree+0x6d)[0xb25e5d]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0x1ba441]
/usr/lib/libstdc++.so.6(_ZdaPv+0x1d)[0x1ba49d]
/usr/lib/libapt-pkg.so.4.10(_ZN12pkgOrderList5DoRunEv+0x158)[0x5d8fc8]
/usr/lib/libapt-pkg.so.4.10(_ZN12pkgOrderList11OrderUnpackEPSs+0x15a)[0x5dadba]
/usr/lib/libapt-pkg.so.4.10(_ZN17pkgPackageManager11GetArchivesEP10pkgAcquireP13pkgSourceListP10pkgRecords+0x21b)[0x5e10cb]
apt-get[0x8056e4e]
apt-get[0x8059090]
/usr/lib/libapt-pkg.so.4.10(_ZN11CommandLine11DispatchArgEPNS_8DispatchEb+0x60)[0x5b6ae0]
apt-get[0x80534fb]
/lib/libc.so.6(__libc_start_main+0xe7)[0xacbce7]
apt-get[0x804e9c1]
```
Its seems to do with the package list, as the error came up right after I ran ```
sudo apt-get update
``` and the traceback mentions GetArchives. Any Ideas? 
And thanks in advance for the help.

---

### Post by plucky on 2011-01-21
What does ```
sudo dpkg -configure -a
``` show you.

---

### Post by Linux000 on 2011-01-21
When I run dpkg, I get nothing, it just returns to a prompt.

---

### Post by Frogs Hair on 2011-01-21
This worked for me .

sudo dpkg --configure -a

sudo apt-get install -f

---

### Post by Linux000 on 2011-01-21
I get the same thing when I run Dpkg, it gives no output... no package outputs, nothing. Then I get to the same point as before in apt-get, only it gives me no traceback, it just stops.

---

### Post by plucky on 2011-01-22
> **Linux000 said:**
> I get the same thing when I run Dpkg, it gives no output... no package outputs, nothing. Then I get to the same point as before in apt-get, only it gives me no traceback, it just stops.

Are you running 11.04 Natty Narwhal?

You could try aptitude if it is installed.I upgraded to Natty and Aptitude is still there,but if you did a clean install of Natty then it might not be there.

---

### Post by Linux000 on 2011-01-22
Right Now I'm running Meerkat, and I do not have aptitude installed.

---

