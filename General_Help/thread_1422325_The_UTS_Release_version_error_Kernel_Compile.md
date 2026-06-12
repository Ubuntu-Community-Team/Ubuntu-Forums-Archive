---
title: "The UTS Release version error Kernel Compile"
date: 2010-03-05
forum: General Help
---

### Post by sondo2121 on 2010-03-05
I get the error
```
make[1]: Leaving directory `/usr/src/linux-2.6.33'
test ! -e scripts/package/builddeb || mv -f scripts/package/builddeb scripts/package/builddeb.kpkg-dist
test ! -e scripts/package/Makefile || test -f scripts/package/Makefile.kpkg-dist || (mv -f scripts/package/Makefile scripts/package/Makefile.kpkg-dist && (echo "# Dummy file "; echo "help:") >  scripts/package/Makefile)
COLUMNS=150 dpkg -l 'gcc*' perl dpkg 'libc6*' binutils make dpkg-dev |\
	 awk '$1 ~ /[hi]i/ { printf("%s-%s\n", $2, $3) }'> debian/buildinfo
uname -a >> debian/buildinfo
echo using the compiler: >> debian/buildinfo
grep LINUX_COMPILER include/linux/compile.h | \
	   sed -e 's/.*LINUX_COMPILER "//' -e 's/"$//' >> debian/buildinfo
grep: include/linux/compile.h: No such file or directory
echo applied kernel patches: >> debian/buildinfo
echo done > debian/stamp/build/kernel
/usr/bin/make -f ./debian/rules 	debian/stamp/binary/pre-linux-image-2.6.33-noipv6
make[1]: Entering directory `/usr/src/linux-2.6.33'
====== making target debian/stamp/install/linux-image-2.6.33-noipv6 [new prereqs: ]======
This is kernel package version 11.015.
echo "The UTS Release version in include/linux/version.h"; echo "	   \"\" "; echo "does not match current version:"; echo "	   \"2.6.33-noipv6\" "; echo "Please correct this."; exit 2
**_The UTS Release version in include/linux/version.h_**
	   "" 
does not match current version:
	   "2.6.33-noipv6" 
Please correct this.
make[1]: *** [debian/stamp/install/linux-image-2.6.33-noipv6] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.33'
make: *** [kernel_image] Error 2

```

I am not using bleeding edge, it's just the most recent stable kernel from kernel.org.

I have compiled kernels before, so I know my process works, but I was wondering if anybody knows if something changed or how to mitigate this error.

Thanks in advance.

---

### Post by sondo2121 on 2010-03-05
This may be related to this bug:

[https://bugs.launchpad.net/kernelcheck/+bug/505125](https://bugs.launchpad.net/kernelcheck/+bug/505125)

If so, does anybody know how to get the most recent version of kernel-package?

(It looks like I have "This is kernel package version 11.015")

EDIT:  I have downloaded the updated kernel-package from: [http://packages.debian.org/squeeze/all/kernel-package/download](http://packages.debian.org/squeeze/all/kernel-package/download) and I am currently compiling my kernel, I'll post my results.

---

### Post by sondo2121 on 2010-03-05
The kernel _did_ compile correctly, although it didn't install correctly.  I got a VSync (kernel sync) error when I tried to boot into it.  

I looked at the sizes of the .deb packages that were created and it turns out the image was ~36MB when it should be around ~370MB...

I am recompiling on a different machine now...

---

### Post by epi 1:10,000 on 2010-03-06
Let me know how it goes. I am having the same problems in 9.10.

---

### Post by sondo2121 on 2010-03-08
> **epi 1:10,000 said:**
> Let me know how it goes. I am having the same problems in 9.10.

Ok, I finally got things working.  I don't think it was an issue with kernel-package...

I was trying to compile 2.6.33 stable vanilla from kernel.org with version 11.xx and 12.xx of kernel-package and it wasn't working.

I decided to try out 2.6.32.9 stable vanilla with 11.xx and it worked, weird, but it did.

_I have a working 2.6.32.9 with IPV6 compiled out if anybody would like it._

```
6.0M 2010-02-20 19:04 linux-headers-2.6.31.12-noipv6_2.6.31.12-noipv6-10.00.Custom_i386.deb
6.2M 2010-03-06 14:31 linux-headers-2.6.32.9-noipv6_2.6.32.9-noipv6-10.00.Custom_i386.deb
372M 2010-02-20 19:03 linux-image-2.6.31.12-noipv6_2.6.31.12-noipv6-10.00.Custom_i386.deb
366M 2010-03-06 14:31 linux-image-2.6.32.9-noipv6_2.6.32.9-noipv6-10.00.Custom_i386.deb
```

Let me know if you are having any issues and maybe I ran into them too.... Hope this helps.

---

### Post by NHclimber on 2010-03-12
Edit: Use the patch in post #8. The one in this post had an error.

This is an issue with kernel-package (<12.032) when building kernel v2.6.33+. The kernel filesystem hierarchy has changed to separate generated header files from repository header files. The debian bug report is here -> [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569)

Don't use those patches though as Karmic's kernel-package is 11.015 and those reports refer to 12.031. You can use the attached patch on Karmic's kernel-package (in /usr/share/kernel-package). But first save the originals (this is what the patch operates against).

```
/usr/share/kernel-package$ cp -v ruleset/misc/version_vars.mk{,.orig}
/usr/share/kernel-package$ cp -v ruleset/targets/common.mk{,.orig}
```Make sure to do 'make-kpkg clean' before rebuilding the kernel to sweep out the stale debian rules from your kernel sources.

---

### Post by Helix7 on 2010-03-18
I ran into the same problem the 2.6.33 kernel gives me that error while trying to compile.. 
Stupid question but how do you apply that patch. ?

---

### Post by NHclimber on 2010-03-20
Before you do this, make sure this is something you really want/need to do. Some packages **will not** build/run in Karmic with a 2.6.33+ kernel. For example, getting the restricted Nvidia driver (any version) to build is a seriously uphill battle for someone totally comfortable running a mixed system. I had to build 185.18.36 from the source package after modifying the Nvidia kernel driver sources because of api differences between 2.6.32 and 2.6.33, plus I had to upgrade dkms to lucid version and modify the Nvidia build.

First, verify you have the version of kernel-package for which the patch is appropriate
```
apt-cache policy kernel-package
```version should be 11.015. Then,
```
cd /usr/share/kernel-package
sudo cp -v ruleset/misc/version_vars.mk{,.orig}
sudo cp -v ruleset/targets/common.mk{,.orig}
sudo patch -p1 -i /where/you/saved/kernel-package-11.015-2.6.33.patch.txt
```Note: in the patch command option list, the -p1 option is -p"one" not -p"ell".

And use this patch instead. The previous patch had an error.

---

### Post by nkrvivek on 2010-03-20
> **NHclimber said:**
> Before you do this, make sure this is something you really want/need to do. Some packages **will not** build/run in Karmic with a 2.6.33+ kernel. For example, getting the restricted Nvidia driver (any version) to build is a seriously uphill battle for someone totally comfortable running a mixed system. I had to build 185.18.36 from the source package after modifying the Nvidia kernel driver sources because of api differences between 2.6.32 and 2.6.33, plus I had to upgrade dkms to lucid version and modify the Nvidia build.

First, verify you have the version of kernel-package for which the patch is appropriate
```
apt-cache policy kernel-package
```version should be 11.015. Then,
```
cd /usr/share/kernel-package
sudo cp -v ruleset/misc/version_vars.mk{,.orig}
sudo cp -v ruleset/targets/common.mk{,.orig}
sudo patch -p1 -i /where/you/saved/kernel-package-11.015-2.6.33.patch.txt
```Note: in the patch command option list, the -p1 option is -p"one" not -p"ell".

And use this patch instead. The previous patch had an error.
I think the previous patch worked perfectly. This one is throwing out an error saying:

Reversed (or previously applied) patch detected!
Hunk #1 FAILED at 333

---

### Post by nkrvivek on 2010-03-20
Its a bug in the kernel-pkg. The new location of utsrelease.h is in include/generated/utsrelease.h So, it can easily be fixed by changing the version_vars.mk file accordingly. No need of any patches.

---

### Post by Whizard72 on 2010-03-25
Really? I have not had any trouble with packages either building or running with the 2.6.33 kernel, neither have I had trouble with the latest Nvidia driver (195.36.15). I'm using 9.04 Jaunty.

> **NHclimber said:**
> Before you do this, make sure this is something you really want/need to do.** Some packages will not build/run in Karmic with a 2.6.33+ kernel.** For example, getting the restricted Nvidia driver (any version) to build is a seriously uphill battle for someone totally comfortable running a mixed system. I had to build 185.18.36 from the source package after modifying the Nvidia kernel driver sources because of api differences between 2.6.32 and 2.6.33, plus I had to upgrade dkms to lucid version and modify the Nvidia build.


---

### Post by sondo2121 on 2010-03-25
> **NHclimber said:**
> Before you do this, make sure this is something you really want/need to do. Some packages **will not** build/run in Karmic with a 2.6.33+ kernel. For example, getting the restricted Nvidia driver (any version) to build is a seriously uphill battle for someone totally comfortable running a mixed system. I had to build 185.18.36 from the source package after modifying the Nvidia kernel driver sources because of api differences between 2.6.32 and 2.6.33, plus I had to upgrade dkms to lucid version and modify the Nvidia build.

First, verify you have the version of kernel-package for which the patch is appropriate
```
apt-cache policy kernel-package
```version should be 11.015. Then,
```
cd /usr/share/kernel-package
sudo cp -v ruleset/misc/version_vars.mk{,.orig}
sudo cp -v ruleset/targets/common.mk{,.orig}
sudo patch -p1 -i /where/you/saved/kernel-package-11.015-2.6.33.patch.txt
```Note: in the patch command option list, the -p1 option is -p"one" not -p"ell".

And use this patch instead. The previous patch had an error.

Thanks, this worked for me.

---

### Post by bipul on 2010-05-21
I was compiling kernel version 2.6.34 stable... there i got the same UTS version mismatch error... I have applied teh patch ... thanks

NOw I have to recompile the stuff to see where it goes

---

### Post by theterabyteboy on 2010-07-08
I am upgrading from 2.6.8-2-386 to 2.6.34.1, which patch do I need and how would I go about applying it? I am using the instructions for updating my kernel on this website: [http://www.debianhelp.co.uk/kernel2.6.htm](http://www.debianhelp.co.uk/kernel2.6.htm)

Thank you for your help

---

### Post by cupofdenial on 2010-11-06
> **nkrvivek said:**
> Its a bug in the kernel-pkg. The new location of utsrelease.h is in include/generated/utsrelease.h So, it can easily be fixed by changing the version_vars.mk file accordingly. No need of any patches.

This solution worked perfectly for me, switching from 2.6.32 to 2.6.36. 

Thanks!

---

### Post by mattypiper on 2011-01-12
> **nkrvivek said:**
> Its a bug in the kernel-pkg. The new location of utsrelease.h is in include/generated/utsrelease.h So, it can easily be fixed by changing the version_vars.mk file accordingly. No need of any patches.

This fixed my issue with building 2.6.37

change include/linux/utsrelease.h to include/generated/utsrelease.h on lines 141 and 142 of debian/ruleset/misc/version_vars.mk

---

