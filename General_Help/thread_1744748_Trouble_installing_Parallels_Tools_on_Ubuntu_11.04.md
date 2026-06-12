---
title: "Trouble installing Parallels Tools on Ubuntu 11.04"
date: 2011-04-30
forum: General Help
---

### Post by bretty511 on 2011-04-30
I am running Ubuntu 11.04 as a Parallels Desktop virtual machine on Mac OSX 10.6. I have Parallels version 6.0.11994. When I try to install Parallels Tools, I get the following output in /var/log/parallels-tools-install.log:

```

Ign http://extras.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://security.ubuntu.com natty-security InRelease
Hit http://extras.ubuntu.com natty Release.gpg
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Hit http://extras.ubuntu.com natty Release
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Hit http://security.ubuntu.com natty-security Release
Hit http://us.archive.ubuntu.com natty Release
Hit http://extras.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty-updates Release
Hit http://extras.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Hit http://security.ubuntu.com natty-security/main Sources
Hit http://security.ubuntu.com natty-security/restricted Sources
Hit http://security.ubuntu.com natty-security/universe Sources
Hit http://security.ubuntu.com natty-security/multiverse Sources
Hit http://security.ubuntu.com natty-security/main i386 Packages
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://security.ubuntu.com natty-security/universe i386 Packages
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Ign http://extras.ubuntu.com natty/main Translation-en
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en
Reading package lists...
Return code from apt-get update is 0
WARNING: The following packages cannot be authenticated!
  dkms
dpkg-preconfigure: unable to re-open stdin: 
Authentication warning overridden.
Selecting previously deselected package dkms.
(Reading database ... 130078 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-5ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-5ubuntu1) ...

Fri Apr 29 20:11:00 PDT 2011
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.38-8-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: error: unknown field 'ioctl' specified in initializer
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: warning: initialization from incompatible pointer type
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [prl_tg] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make: *** [all] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2011-04-29T20:17:19-0700: 

Parallels Tools 6.0.11800.593005 Installer started.
2011-04-29T20:17:35-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Fri Apr 29 20:17:35 PDT 2011
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.38-8-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: error: unknown field ‘ioctl’ specified in initializer
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: warning: initialization from incompatible pointer type
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [prl_tg] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make: *** [all] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2011-04-29T20:17:41-0700: execCmd: ./install --install [143]
2011-04-29T20:17:41-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2011-04-29T20:23:25-0700: 

Parallels Tools 6.0.11800.593005 Installer started.
2011-04-29T20:23:29-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Fri Apr 29 20:23:29 PDT 2011
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.38-8-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: error: unknown field ‘ioctl’ specified in initializer
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: warning: initialization from incompatible pointer type
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [prl_tg] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make: *** [all] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2011-04-29T20:23:37-0700: execCmd: ./install --install [143]
2011-04-29T20:23:37-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2011-04-29T20:35:26-0700: 

Parallels Tools 6.0.11800.593005 Installer started.
2011-04-29T20:35:28-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Fri Apr 29 20:35:28 PDT 2011
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.38-8-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: error: unknown field ‘ioctl’ specified in initializer
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:964:2: warning: initialization from incompatible pointer type
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [prl_tg] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make: *** [all] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2011-04-29T20:35:33-0700: execCmd: ./install --install [143]
2011-04-29T20:35:33-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2011-04-29T21:31:16-0700: 

Parallels Tools 6.0.11994.637263 Installer started.
2011-04-29T21:31:18-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Fri Apr 29 21:31:18 PDT 2011
Start installation or upgrade of Guest Tools
Failed express installation is detected!
Trying to restore /etc/rc.local and other stuff
mv: cannot stat `/opt/prl-tools-installer/S*gdm': No such file or directory
mv: cannot stat `/opt/prl-tools-installer/S*kdm': No such file or directory
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.38-8-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:972:2: error: unknown field ‘ioctl’ specified in initializer
/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.c:972:2: warning: initialization from incompatible pointer type
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [prl_tg] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make: *** [all] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2011-04-29T21:31:27-0700: execCmd: ./install --install [143]
2011-04-29T21:31:27-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.

```

Can someone help me troubleshoot?

Thank you very much.

---

### Post by &#31934;&#33521;&#35302;&#25163;&#24618; on 2011-05-01
I'm afraid parallels doesn't support Ubuntu 11.04
see the system requirements
[http://www.parallels.com/products/desktop/pd4wl/sys-requirements/](http://www.parallels.com/products/desktop/pd4wl/sys-requirements/)

---

### Post by asciimo on 2011-05-04
11.04 seems to be working fine for me, but I get the same error when I attempt to install Parallels Tools.  Also, I'm told, that Unity won't run on my hardware (13" MacBook Air, 2.13 GHz Core 2 Duo, 4GB).  So, it might not be "supported," but it's functional.

---

### Post by Joji on 2011-05-10
Got exactly the same problem. Same versions of Parallels and OSX. 
What's the difference with Ubuntu 10.10 which is officially supported by Parallels 6? 
My Natty is working fine, however having the Tools installed would bring a better user experience. For the time being I'm obliged to press Ctrl+Alt to release my mouse outside of the Natty window (not very convenient). I haven't raised the question to Parallels support yet. But will do if there is no workaround. Any help welcome!

---

### Post by scyleung on 2011-05-15
I am guessing it is because 11.04 is not supported yet, seem like Virtual Box is the only VM software between VMware/Parallels/Virtual Box that support 11/04, but so far, it seem to run better in Parallels even without the tools/addition.

---

### Post by Bruce Page on 2011-07-19
Does anyone know if this problem has been resolved yet?

---

### Post by M-Rick on 2011-07-22
No it's not and they don't care.

They ask you for support ticket submitting, they are not aware of the problem, and I am probably the only one on hearth having this problem following them ....

"Hey M-Rick,

Did you open a support request? [http://www.parallels.com/support/request](http://www.parallels.com/support/request)

Others who have downloaded the latest updates have experienced success with PT on Ubuntu, so you're case could be unique.

Keep me in the loop. Would love to help out."

It works only if you will not use Unity 3D.

They don't care, they wait till version 7 is out, and magically, the bug will be resolved in version 7 but of course you'll have to pay for it...

---

