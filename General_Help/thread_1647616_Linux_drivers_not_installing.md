---
title: "Linux drivers not installing"
date: 2010-12-17
forum: General Help
---

### Post by kilerzkof on 2010-12-17
hi i just tried to install th ecatalyst 10.12  (ati-driver-installer-10-12-x86.x86_64.run) using sudo bash but i keep getting this error in the log: 


[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.35-23-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_debug.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_ioctl.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_io.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_pci.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_str.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_wait.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
build succeeded with return value 0
duplicating results into driver repository...
done.
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
- recreating module dependency list
- trying a sample load of the kernel modules
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.
[Reboot] Kernel Module : update-initramfs

---

### Post by kilerzkof on 2010-12-17
anyone?

---

### Post by PhantmKllr on 2010-12-17
What graphics card are you using? If you're using a legacy ATI card, it's best if you use the Open Source drivers.

---

### Post by kilerzkof on 2010-12-17
> **PhantmKllr said:**
> What graphics card are you using? If you're using a legacy ATI card, it's best if you use the Open Source drivers.

radeon hd 6850

---

### Post by PhantmKllr on 2010-12-17
What version of Ubuntu are you running? Have you upgraded from previous versions, or is this a fresh install?

---

### Post by kilerzkof on 2010-12-17
> **PhantmKllr said:**
> What version of Ubuntu are you running? Have you upgraded from previous versions, or is this a fresh install?

fresh install ubuntu 10.10

---

### Post by PhantmKllr on 2010-12-17
It seems as if you're in a real pickle there. Are you sure you got your driver from the ATI website?

---

### Post by kilerzkof on 2010-12-17
i downloaded 10.12 not from the amd website, because when i check amd drivers put in hd 6800 linux does not pop up, so im not sure if it is supported yet,....

---

### Post by kilerzkof on 2010-12-17
i used this link [http://www.phoronix.com/scan.php?page=news_item&px=ODkwNg](http://www.phoronix.com/scan.php?page=news_item&px=ODkwNg)

which then sent me to thins link to download it [http://www.phoronix.com/forums/showthread.php?t=27750](http://www.phoronix.com/forums/showthread.php?t=27750)

---

### Post by PhantmKllr on 2010-12-17
> **kilerzkof said:**
> i downloaded 10.12 not from the amd website, because when i check amd drivers put in hd 6800 linux does not pop up, so im not sure if it is supported yet,....
Yup. I checked the website, and the 6000 HD series is not yet supported under Linux. I guess that you're going to have to use the Open Soruce drivers. Sorry that I couldn't help you out.

---

### Post by kilerzkof on 2010-12-17
no problem :( ill just have to wait, i dont think there are open source drivers yet..... not that i found anyway,

---

### Post by PhantmKllr on 2010-12-17
If you can see graphics on you're screen, then you're using the Open Source drivers. They're the ones that come with Ubuntu. Just saying. ;)

---

### Post by kilerzkof on 2010-12-17
> **PhantmKllr said:**
> If you can see graphics on you're screen, then you're using the Open Source drivers. They're the ones that come with Ubuntu. Just saying. ;)

well i can see the screen, but i cant use 3d effects it just says searching for drivers/ no drivers found/ effects can not be used

---

### Post by hawthornso23 on 2010-12-17
Just a thought, but did you uninstall any previous fglrx drivers first? It sounds like it is complaining about running into an existing kernel module.

I've just successfully installed 10.12 using these instructions

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

but mine is an HD4650, so YMWV.

Good Luck

Tip: If you get it to install and find your window decorations disappear in compiz, try disabling the reflection plugin. It seems to have a weird problem with the 10.12 fglrx driver that causes window decorations to become completely transparent.

---

### Post by kilerzkof on 2010-12-17
> **hawthornso23 said:**
> Just a thought, but did you uninstall any previous fglrx drivers first? It sounds like it is complaining about running into an existing kernel module.

I've just successfully installed 10.12 using these instructions

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

but mine is an HD4650, so YMWV.

Good Luck

Tip: If you get it to install and find your window decorations disappear in compiz, try disabling the reflection plugin. It seems to have a weird problem with the 10.12 fglrx driver that causes window decorations to become completely transparent.

when installing fglrx i get this:


Selecting previously deselected package patch.
(Reading database ... 145913 files and directories currently installed.)
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.2-3_i386.deb) ...
Selecting previously deselected package libmng1.
Unpacking libmng1 (from .../libmng1_1.0.10-1_i386.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.791-0ubuntu1~xup~maverick_i386.deb) ...
restore of system environment completed

Error! There are no instances of module: fglrx
8.801 located in the DKMS tree.
Errors during DKMS module removal

---

### Post by PhantmKllr on 2010-12-18
> **kilerzkof said:**
> when installing fglrx i get this:


Selecting previously deselected package patch.
(Reading database ... 145913 files and directories currently installed.)
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.2-3_i386.deb) ...
Selecting previously deselected package libmng1.
Unpacking libmng1 (from .../libmng1_1.0.10-1_i386.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.791-0ubuntu1~xup~maverick_i386.deb) ...
restore of system environment completed

Error! There are no instances of module: fglrx
8.801 located in the DKMS tree.
Errors during DKMS module removal
Hmm, that sounds like that the fglrx kernel module isn't loading at start-up. Unfortunately, I don't know much about kernel modules. :( sorry.

---

