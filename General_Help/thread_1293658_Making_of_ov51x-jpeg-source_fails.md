---
title: "Making of ov51x-jpeg-source fails"
date: 2009-10-17
forum: General Help
---

### Post by exodus on 2009-10-17
Greetings folks!

I'm trying to get my Creative Labs Inc Webcam VF0350 to work in Ubuntu Karmic Koala beta! I know that at this point you might think the beta might have bugs, but I thought I'd make my post anyway.

I installed the ov51x-jpeg-source from the Synaptic Package Manager. It installed without any problems. Then I tried running the following commands to make the drivers.

```
sudo module-assistant a-i ov51x-jpeg
```

The process fails at this step. I would have done the following if the above step was successful

```
sudo depmod -a
sudo modprobe ov51x-jpeg
```

Here is what I get when the making fails:

Build of the package ov51x-jpeg-source failed! How do you wish to proceed?
I choose view log and here is what I get.
```

for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-14-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.31-14-generic/g ;s/#KVERS#/2.6.31-14-generic/g ; s/_KVERS_/2.6.31-14-generic/g ; s/##KDREV##/2.6.31-14.48/g ; s/#KDREV#/2.6.31-14.48/g ; s/_KDREV_/2.6.31-14.48/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/ov51x-jpeg'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
make[1]: Leaving directory `/usr/src/modules/ov51x-jpeg'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ov51x-jpeg'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-14-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.31-14-generic/g ;s/#KVERS#/2.6.31-14-generic/g ; s/_KVERS_/2.6.31-14-generic/g ; s/##KDREV##/2.6.31-14.48/g ; s/#KDREV#/2.6.31-14.48/g ; s/_KDREV_/2.6.31-14.48/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
/usr/bin/make -w -f debian/rules clean
make[2]: Entering directory `/usr/src/modules/ov51x-jpeg'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: Nothing to be done for `kdist_config'.
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make KERNEL_DIR=/usr/src/linux KDIR=/usr/src/linux KVERS=2.6.31-14-generic
make[2]: Entering directory `/usr/src/modules/ov51x-jpeg'
/usr/bin/make -C /usr/src/linux M=/usr/src/modules/ov51x-jpeg modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘create_proc_ov511_cam’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:677: error: implicit declaration of function ‘info’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:681: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:689: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:700: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:712: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘proc_ov511_create’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:766: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘ov51x_clear_snapshot’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:1691: error: implicit declaration of function ‘warn’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: error: too many arguments to function ‘video_usercopy’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: At top level:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
make[4]: *** [/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o] Error 1
make[3]: *** [_module_/usr/src/modules/ov51x-jpeg] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make: *** [kdist_build] Error 2
```

As an alternative I even tried installing the hacked source from rastageeks and I seem to be getting a similar error. It fails when I make the source.

I have all the dependencies installed. At least thats what I think!

If it would help, here is the output of my lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 041e:4067 Creative Technology, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Any help would be greatly appreciated. Thanks in advance for your time and effort.

---

### Post by Gorbayov on 2009-10-30
wont compile on 2.6.31 kernel

---

### Post by exodus on 2009-10-30
thanks for your reply m8...

is there any workaround for this? or is there no way to get my current webcam (VF0350) working on ubuntu 9.10...

if that is the case, rather than trying i would just get a new one..

it is just that i need to know definitively..

---

### Post by afallenhope on 2009-11-21
Hey guys,

I created a patch which seems to work with a bunch of kernels so you can try it and report whether or not it's successful or not. Since I can't upload patches on here you can find the [patch here]("http://www.afallenhope.com"). I hope this helps!

Cheers,
afh

---

### Post by Satyg on 2009-11-24
> **afallenhope said:**
> Hey guys,

I created a patch which seems to work with a bunch of kernels so you can try it and report whether or not it's successful or not. Since I can't upload patches on here you can find the [patch here]("http://www.afallenhope.com"). I hope this helps!

Cheers,
afh

I tried your patch and everything compiled.
Although my cam now actually shows something - it only shows a garbled blob of colors, mostly green and a little red.
(Yes, I tried to unplug/plug my camera several times.)
Drats. :(

---

### Post by ajhinz on 2010-02-18
Just chiming in to say that the ov51x-jpeg-source module + the patch by afallenhope worked for my Createive Cam Notebook Pro [VF0400] webcam on ubuntu 9.10 (AMD64).

---

### Post by shoryuken on 2010-08-22
> **afallenhope said:**
> Hey guys,

I created a patch which seems to work with a bunch of kernels so you can try it and report whether or not it's successful or not. Since I can't upload patches on here you can find the [patch here]("http://www.afallenhope.com"). I hope this helps!

Cheers,
afh

Hi,
I'd appreciate any guidance or suggestions to try o resolve this. I've tried using the patch and it fails to work. I'm running Lucid with 2.6.32-24-generic kernel.

Here is what I get when I try to apply the patch:
```

patching file ov51x-jpeg-1.5.9_patched/ov511-decomp.c
Hunk #1 FAILED at 508.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov511-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov518-decomp.c
Hunk #1 FAILED at 1488.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov518-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov519-decomp.c
Hunk #1 FAILED at 1534.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov519-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov51x-jpeg-core.c
Hunk #1 FAILED at 12.
Hunk #2 FAILED at 539.
Hunk #3 FAILED at 678.
Hunk #4 FAILED at 686.
Hunk #5 FAILED at 697.
Hunk #6 FAILED at 709.
Hunk #7 FAILED at 762.
Hunk #8 FAILED at 5733.
Hunk #9 FAILED at 5804.
Hunk #10 FAILED at 5850.
Hunk #11 FAILED at 6355.
Hunk #12 FAILED at 6372.
Hunk #13 FAILED at 6383.
Hunk #14 FAILED at 6624.
Hunk #15 FAILED at 8374.
15 out of 15 hunks FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov51x-jpeg-core.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov51x-jpeg.h
Hunk #1 FAILED at 63.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov51x-jpeg.h.rej


```


Without the patch I get the following error when I try to compile ov51x
```

make -C /lib/modules/2.6.32-24-generic/build M=/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.o
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘create_proc_ov511_cam’:
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:677: error: implicit declaration of function ‘info’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:681: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:689: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:700: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:712: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘proc_ov511_create’:
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:766: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘ov51x_clear_snapshot’:
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:1691: error: implicit declaration of function ‘warn’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:6386: error: too many arguments to function ‘video_usercopy’
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c: At top level:
/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
make[2]: *** [/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/arash/Desktop/Webcam/ov51x-jpeg-1.5.9/ov51x-jpeg] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2

```

TIA

---

### Post by guysoft on 2011-02-14
> **shoryuken said:**
> Hi,
I'd appreciate any guidance or suggestions to try o resolve this. I've tried using the patch and it fails to work. I'm running Lucid with 2.6.32-24-generic kernel.

Here is what I get when I try to apply the patch:
[CODE]
patching file ov51x-jpeg-1.5.9_patched/ov511-decomp.c
Hunk #1 FAILED at 508.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov511-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov518-decomp.c
Hunk #1 FAILED at 1488.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov518-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov519-decomp.c
Hunk #1 FAILED at 1534.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov519-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov51x-jpeg-core.c
Hunk #1 FAILED at 12.
Hunk #2 FAILED at 539.
Hunk #3 FAILED at 678.
Hunk #4 FAILED at 686.
Hunk #5 FAILED at 697.
Hunk #6 FAILED at 709.
Hunk #7 FAILED at 762.
Hunk #8 FAILED at 5733.
Hunk #9 FAILED at 5804.
Hunk #10 FAILED at 5850.
Hunk #11 FAILED at 6355.
Hunk #12 FAILED at 6372.
Hunk #13 FAILED at 6383.
Hunk #14 FAILED at 6624.
Hunk #15 FAILED at 8374.
15 out of 15 hunks FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov51x-jpeg-core.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov51x-jpeg.h
Hunk #1 FAILED at 63.
1 out of 1 hunk FAILED -- saving rejec
ts to file ov51x-jpeg-1.5.9_patched/ov51x-jpeg.h.rej

Same problem in Debian Sid

---

### Post by prostar on 2011-05-14
Did you get anywhere with this?

---

### Post by David Andersson on 2011-12-01
> **shoryuken said:**
> 
Here is what I get when I try to apply the patch:
```

patching file ov51x-jpeg-1.5.9_patched/ov511-decomp.c
Hunk #1 FAILED at 508.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov511-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov518-decomp.c
Hunk #1 FAILED at 1488.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov518-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov519-decomp.c
Hunk #1 FAILED at 1534.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov519-decomp.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov51x-jpeg-core.c
Hunk #1 FAILED at 12.
Hunk #2 FAILED at 539.
Hunk #3 FAILED at 678.
Hunk #4 FAILED at 686.
Hunk #5 FAILED at 697.
Hunk #6 FAILED at 709.
Hunk #7 FAILED at 762.
Hunk #8 FAILED at 5733.
Hunk #9 FAILED at 5804.
Hunk #10 FAILED at 5850.
Hunk #11 FAILED at 6355.
Hunk #12 FAILED at 6372.
Hunk #13 FAILED at 6383.
Hunk #14 FAILED at 6624.
Hunk #15 FAILED at 8374.
15 out of 15 hunks FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov51x-jpeg-core.c.rej
patching file ov51x-jpeg-1.5.9_patched/ov51x-jpeg.h
Hunk #1 FAILED at 63.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg-1.5.9_patched/ov51x-jpeg.h.rej


```

All hunks failed for me when i padched in the wrong directory. Make sure you have cd:ed to the right directory and makt sure the subdirectory there is called "ov51x-jpeg-1.5.9" (you must rename it if you unpacked it from package ov51x-jpeg-source).

(Still working on getting any images from a brand-less slide-scanner with an OmniVision chip.)

---

