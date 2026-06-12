---
title: "utsrelease.h not found when trying to install fglrx in 10.04."
date: 2010-06-27
forum: General Help
---

### Post by GraysonPeddie on 2010-06-27
Hi. I need support for adjusting over/underscan for my Mitsibushi WD-Y577 57" DLP HDTV (a breed between WD-57733 and WD-57734), because the open source ATI Radeon driver does not include it. When I attempt to install fglrx, here's what I'm getting:

apt-get install fglrx
```
Loading new fglrx-8.723.1 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.33.5-rt23
Building for architecture x86_64
Building initial module for 2.6.33.5-rt23

Error! Bad return status for module build on kernel: 2.6.33.5-rt23 (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33.5-rt23
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

file: /var/lib/dkms/fglrx/8.723.1/build/make.log
```
DKMS make.log for fglrx-8.723.1 for kernel 2.6.33.5-rt23 (x86_64)
Sun Jun 27 18:57:08 EDT 2010 AMD kernel module generator version 2.1 
cat: /lib/modules/2.6.33.5-rt23/build/include/linux/utsrelease.h: No such file or directory
Error: kernel includes at /lib/modules/2.6.33.5-rt23/build/include do not match current kernel.
they are versioned as "" instead of "2.6.33.5-rt23".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux
```

I did adjust symlinks properly.

I have compiled 2.6.33.5 from source and patched it with 2.6.33.5-rt23. I have adjusted features take a lot of things off that I don't need. I need the real-time kernel for music creation using JACK (Jack Audio Control Kit).

Adjusting over/underscan requires an AMD Catalyst Control Center. Will there be future open-source ATI drivers that allow me to correct my display without having to change modelines in xorg? It will take a lot of trial and error to figure this out for my display.

Note that even if I did install the kernel headers for 2.6.32-23-preempt or 2.6.33-23-realtime (depending on what I use), fglrx module will still fail to install, even if I install linux-source.

I'm confused. I do want fglrx and I do need the real-time/low-latency kernel for music creation under Ubuntu 10.04.

Update:

Okay, if you create a utsrelease.h header file inside /usr/include/linux directory, you can write out like this:

```
#define UTS_RELEASE "2.6.33.5-rc3" # replace the version number for your running kernel.
```

You can then reinstall fglrx, but then I get this:

```
DKMS make.log for fglrx-8.723.1 for kernel 2.6.33.5-rt23 (x86_64)
Sun Jun 27 19:45:11 EDT 2010
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.33.5-rt23/build SUBDIRS=/var/lib/dkms/fglrx/8.723.1/build/2.6.x modules
make[1]: Entering directory `/home/grayson/Downloads/src/linux-2.6.33.5'
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:31:28: error: linux/autoconf.h: No such file or directory
In file included from /var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:443:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c: In function &#8216;fglrx_pci_suspend&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:833: error: implicit declaration of function &#8216;acquire_console_sem&#8217;
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:855: error: implicit declaration of function &#8216;release_console_sem&#8217;
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c: In function &#8216;firegl_init_module&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:1028: error: expected expression before &#8216;{&#8217; token
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c: In function &#8216;KCL_SetPageCache_Array&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:1316: warning: passing argument 1 of &#8216;KCL_ConvertPageToKernelAddress&#8217; makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.h:325: note: expected &#8216;void *&#8217; but argument is of type &#8216;long unsigned int&#8217;
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c: In function &#8216;__ke__cmpxchg&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:1473: error: variable or field &#8216;__ret&#8217; declared void
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:1473: error: variable or field &#8216;__old&#8217; declared void
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:1473: error: variable or field &#8216;__new&#8217; declared void
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c: In function &#8216;KAS_Mutex_Initialize&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:5051: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.723.1/build/2.6.x] Error 2
make[1]: Leaving directory `/home/grayson/Downloads/src/linux-2.6.33.5'
make: *** [kmod_build] Error 2
build failed with return value 2
```

Hmm... One thing I'd like to ask is why is it compiling firegl_public.c? I'm not using ATI FireGL. I have an integrated ATI chipset (Radeon HD 3200).

---

### Post by hfranco75 on 2010-06-30
Same problem here... are there some news?

---

### Post by Lantash on 2010-08-28
I'm experiencing the very same problem on Ubuntu 10.10 and thus reported it: [https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/625787](https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/625787)

After the failed configuration of the fglrx package, the system fails to boot the graphical environment. Do you know how to fix the system's state from the terminal, avoiding a tedious fresh installation?

---

### Post by Devport on 2010-08-28
> **Lantash said:**
> I'm experiencing the very same problem on Ubuntu 10.10 and thus reported it: [https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/625787](https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/625787)

After the failed configuration of the fglrx package, the system fails to boot the graphical environment. Do you know how to fix the system's state from the terminal, avoiding a tedious fresh installation?
```
sudo apt-get remove fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo restart gdm
```
Got my Maverick to use the radeon driver again. A newer fglrx installs fine ( including module building ) but does not work with xorg 1.9 yet.

**Lucid users may try to add that ppa to get a package working with newer kernels :**

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by holtz on 2010-09-23
Same problem here.  I was trying to upgrade to 2.6.35 to fix a kernel problem I have when running some programs under wine.  But I need fglrx.

---

### Post by holtz on 2010-09-23
Possible workaround from 

[http://bugs.gentoo.org/show_bug.cgi?id=297322](http://bugs.gentoo.org/show_bug.cgi?id=297322)


```
cd /usr/src/linux/include/linux
ln -s ../generated/autoconf.h .
ln -s ../generated/utsrelease.h .
```


Okay, that got me to the same point as the post above.  Then I found:

[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg270029.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg270029.html)

He proposes a patch to work around the error and says it's been put into Debian.  Perhaps it hasn't gotten to Ubuntu yet?  Or is this really ATI's responsibility?

---

### Post by karlwilbur on 2011-03-08
> **holtz said:**
> Possible workaround from 

[http://bugs.gentoo.org/show_bug.cgi?id=297322](http://bugs.gentoo.org/show_bug.cgi?id=297322)


```
cd /usr/src/linux/include/linux
ln -s ../generated/autoconf.h .
ln -s ../generated/utsrelease.h .
```



I fetched fglrx-8.812 then after doing the above, I copied fglrx-8.812 to fglrx-8.723.1 directory and then everything seems to have installed just fine.
```

sudo mv /usr/src/fglrx-8.723.1{,-old}
sudo cp -R /usr/src/fglrx-8.{812,723.1}
sudo aptitude install fglrx fglrx-amdcccle

```

---

