---
title: "kernel 2.6.16.5"
date: 2006-04-17
forum: General Help
---

### Post by nosiad2 on 2006-04-17
hi, i would like to ugrade my kernel to the latest stable version, which kernel.org reports as version 2.6.16.5. I am following the tutorial found at [http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560)
but i ran into trouble when trying to find the performance patch for kernel 2.6.16.5.
I tried using the latest performance patch, 'patch-2.6.16-cks5.bz2', but i got errors when i was building the kernel.
my question is, does kernel 2.6.16.5 include the performance patches? or do i have to wait longer before i can find the performance patches online.

by the way, i am currently building kernel 2.6.16.5 without the performance patches, and no errors have occured thus far. if the performance patches are not included with the 2.6.16.5 release, what benefits will i lose?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=nosiad2]hi, i would like to ugrade my kernel to the latest stable version, which kernel.org reports as version 2.6.16.5. I am following the tutorial found at [http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560)
but i ran into trouble when trying to find the performance patch for kernel 2.6.16.5.
I tried using the latest performance patch, 'patch-2.6.16-cks5.bz2', but i got errors when i was building the kernel.
my question is, does kernel 2.6.16.5 include the performance patches? or do i have to wait longer before i can find the performance patches online.

by the way, i am currently building kernel 2.6.16.5 without the performance patches, and no errors have occured thus far. if the performance patches are not included with the 2.6.16.5 release, what benefits will i lose?[/QUOTE]
You can just skip the patch and then when you configure the kernel you can configure it for maxium proformance. You won't really loose anything either. I am running the 2.6.17-rc1 kernel that I compilied last night and it is unpatched but it works fine. I am getting the same/better performance then the patched kernel because I custom compilied it. That patch is only for 2.6.16 too. Not 2.6.16.5 :)

---

### Post by tseliot on 2006-04-17
You should: 
1) download kernel 2.6.16.0
2) download the following patch:
[http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck5/patch-2.6.16-ck5.bz2]("http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck5/patch-2.6.16-ck5.bz2")
3) apply the patch to that kernel

Explanation:
Thanks to the patch your kernel will become like a 2.6.15.5 + the advantages of Kolivas' patch.

Kolivas' patches must be applied to the 1st release of a series of kernels. For example, for kernel 2.6.16.9 (which has not been released) you would use a 2.6.16.0 + the related Kolivas patch (ck9 ???)

---

### Post by ububaba on 2006-04-17
[QUOTE=tseliot]You should: 
1) download kernel 2.6.16.0
2) download the following patch:
[http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck5/patch-2.6.16-ck5.bz2]("http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck5/patch-2.6.16-ck5.bz2")
3) apply the patch to that kernel

Explanation:
Thanks to the patch your kernel will become like a 2.6.15.5 + the advantages of Kolivas' patch.

Kolivas' patches must be applied to the 1st release of a series of kernels. For example, for kernel 2.6.16.9 (which has not been released) you would use a 2.6.16.0 + the related Kolivas patch (ck9 ???)[/QUOTE]

Where can a noob learn about patching a Kernel? Any link on this simple
operartion? Thanks

---

### Post by tseliot on 2006-04-19
[QUOTE=ububaba]Where can a noob learn about patching a Kernel? Any link on this simple
operartion? Thanks[/QUOTE]
You can try this guide of mine:
[HOWTO: Kernel Compilation for Newbies]("http://www.ubuntuforums.org/showthread.php?t=85064")

and have a look at the section "NOTE: HOWTO compile from a vanilla kernel from kernel.org"

---

### Post by ububaba on 2006-04-19
[QUOTE=tseliot]You can try this guide of mine:
[HOWTO: Kernel Compilation for Newbies]("http://www.ubuntuforums.org/showthread.php?t=85064")

and have a look at the section "NOTE: HOWTO compile from a vanilla kernel from kernel.org"[/QUOTE]
Thanks for the response. I followed [COLOR="Red"]Kernel Compilation [/COLOR] but when I reached: $ ls
kernel-headers-2.6.12-ububaba_10.00.Ububaba_i386.deb
kernel-image-2.6.12-ububaba_10.00.Ububaba_i386.deb
linux
linux-headers-2.6.12-10
linux-headers-2.6.12-10-686
linux-headers-2.6.12-10-686-smp
linux-headers-2.6.12-9
linux-headers-2.6.12-9-686
linux-headers-2.6.12-9-686-smp
linux-patches
linux-source-2.6.12
linux-source-2.6.12.tar.bz2
rpm
ububaba@root:/usr/src$ sudo dpkg -i ndiswrapper-modules-2.6.12-ububaba_1.1-4ubuntu2+10.00.Ububaba_i386.deb
dpkg: error processing ndiswrapper-modules-2.6.12-ububaba_1.1-4ubuntu2+10.00.Ububaba_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-modules-2.6.12-ububaba_1.1-4ubuntu2+10.00.Ububaba_i386.deb

.....this is what happend. Before this step there were no objections at all.:-k

---

