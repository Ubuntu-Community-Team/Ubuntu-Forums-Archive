---
title: "Driver compile problem with autoconf.h and version.h"
date: 2010-10-15
forum: General Help
---

### Post by nidzo732 on 2010-10-15
I have a conexant modem and i want to make 
it work(just for fun, i have DSL). The linuxant driver works but i want full 56k. I tried ubuntu help
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant) and there was alink for some Dell driver.
I've compiled and installed the Dell successfully but when i run
"hsfconfig" i get this 

------------------------------------------------------------------------------------------------------------
No pre-built modules for: Ubuntu-10.10 linux-2.6.35-22-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.35-22-generic/build] 

WARNING: missing file /lib/modules/2.6.35-22-generic/build/include/linux/autoconf.h
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.35-22-generic was found.
Would you like to try using it (in a temporary kernel tree)? [yes] 

i enter yes and it says 
Unable to prepare temporary kernel tree

First, ensure that the proper kernel source and compiler packages
from your distribution vendor and/or the community are installed.

The Linux kernel can then be reconfigured by running "make menuconfig"
under the kernel source directory (usually /usr/src/linux).

Verify that the proper options for your system are selected.

Then compile and install your new kernel (for more information about
this procedure, see the README file under the kernel source directory),
reboot the system using the new kernel, and re-run "hsfconfig".
-------------------------------------------------------------------------------------------------------------

I've made an empty autoconf.h file but then hsfconfig said

-------------------------------------------------------------------------------------------------------------
WARNING: the kernel version () defined in
/lib/modules/2.6.35-22-generic/build/include/linux/version.h
does not match the currently running kernel (2.6.35-22-generic)
The cause of this problem is an incorrect kernel source path.
Please check that /lib/modules/2.6.35-22-generic/build points to the right tree.
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.35-22-generic was found.
Would you like to try using it (in a temporary kernel tree)? [yes] 
-------------------------------------------------------------------------------------------------------------

I entered yes and it failed again.
Any help. I've installed linux sources and build essential.
Should i compile the kernel and then run hsfconfig?:confused:

---

### Post by nidzo732 on 2010-10-16
32 views and nothing:mad:

BUMP

---

### Post by p12i on 2010-10-16
First of all, do you have kernel source??
aptitude install linux-source

cd /usr/src/linux

# copy running config 
cp  /boot/config-2.6.35-22-generic .config

#build new kernel
make 

After this try, once again.

---

### Post by vaikz on 2010-10-18
@nidzo732
I'm experiencing the same situation and until now wasn't able to fix this.

@p12i
```
cd /usr/src/linux
```
can't locate this folder. all inside were the linux headers and source. do I
have to create a folder? Or save to the linux source?

---

### Post by lamp20 on 2010-10-30
Hi

sudo -s    
cd /lib/modules/$(uname -r)/build/include/linux    
ln -s ../generated/utsrelease.h    
ln -s ../generated/autoconf.h

my problem solved

tanks


[http://superuser.com/questions/199365/vmware-linux-headers-not-found-for-ubuntu-10-10](http://superuser.com/questions/199365/vmware-linux-headers-not-found-for-ubuntu-10-10)

---

### Post by Ganton on 2010-11-10
Thanks!

With the information given by Diaco, Lamp20 and the writers of [http://help.ubuntu.com/community/DialupModemHowto/Conexant](http://help.ubuntu.com/community/DialupModemHowto/Conexant) I have used a USB winmodem with a conexant driver.

When I plugged that modem in the computer with Maverick, I executed ```
lsusb
``` and it said:
> [...]
Bus 003 Device 003: ID 0572:1300 Conexant Systems (Rockwell), Inc. Softk56 Data Fax Voice CARP
[...]
so I knew that the HSF modem was recognized by the system.

I upgraded the system 
```
sudo apt-get update && sudo apt-get dist-upgrade
```

I checked that I had no previous Conexant drivers installed. For example: if I had seen a file "/usr/sbin/hsfconfig", I would have thought that something was still installed.

I made sure that I had gcc prepared, executing
```
sudo apt-get install gcc
```

Then I executed those steps told there:
```
sudo -s
cd /lib/modules/$(uname -r)/build/include/linux
ln -s ../generated/utsrelease.h
ln -s ../generated/autoconf.h
exit

```

I prepared the files for the compilation, executing
```
mkdir ~/conexant_modem
cd ~/conexant_modem
wget http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09oem.tar.gz
tar xzf hsfmodem-7.68.00.09oem.tar.gz
wget http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip
unzip hsfmodem-7.80.02.05-DiacoEdition.zip
```
and then
```
cp -pR hsfmodem-7.80.02.05-DiacoEdition/modules/imported/include/framewrk.h hsfmodem-7.68.00.09oem/modules/imported/include/framewrk.h
cp -pR hsfmodem-7.80.02.05-DiacoEdition/modules/imported/include/osservices.h hsfmodem-7.68.00.09oem/modules/imported/include/osservices.h

```
*A note for the curious ones: those two files were the different ones between the directories "hsfmodem-7.68.00.09oem/modules/imported" and "hsfmodem-7.80.02.05-DiacoEdition/modules/imported"*.

I executed
```
wget http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz
```
*A note for the curious ones: that file was the newest one in [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) *

And then
```
tar xzf hsfmodem-7.80.02.06full.tar.gz
rm -r hsfmodem-7.80.02.06full/modules/imported
cp -R hsfmodem-7.68.00.09oem/modules/imported hsfmodem-7.80.02.06full/modules/

```

I cleaned the directory
```

rm -rf hsfmodem-7.68.00.09oem
rm -rf hsfmodem-7.80.02.05-DiacoEdition
rm hsfmodem-7.68.00.09oem.tar.gz
rm hsfmodem-7.80.02.05-DiacoEdition.zip
rm hsfmodem-7.80.02.06full.tar.gz

```

And finally
```

cd hsfmodem-7.80.02.06full
sudo make install
sudo hsfconfig

```

It asked "Where is the linux source build directory that matches your running kernel?", then I simply pressed the return key to accept the default answer.

I executed
```
dmesg
```
and at the end I saw
```

    [ 8065.844120] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
    [ 8065.844334] Disabling lock debugging due to kernel taint
    [ 8067.075412] usbcore: registered new interface driver hsfusbcd2
    [ 8159.794167] usb 3-2.2: new full speed USB device using uhci_hcd and address 3
    [ 8161.536542] ttySHSF0 at MMIO 0x0 (irq = 0) is a Conexant HSF softmodem (USB-0572:1300)
    [ 8165.066453] usbcore: deregistering interface driver hsfusbcd2
    [ 8165.169348] usb 3-2.2: reset full speed USB device using uhci_hcd and address 3
    [ 8167.911599] ttySHSF0 at MMIO 0x0 (irq = 0) is a Conexant HSF softmodem (USB-0572:1300)
    [ 8167.921614] usbcore: registered new interface driver hsfusbcd2

``` which meant, among other things, that the USB modem was detected at /dev/ttySHSF0, so I could use kppp (for example) and configure it specifying that the modem was at /dev/ttySHSF0.

Note: as they said in [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant): "*do not delete or move the source tree* [in our case: ~/conexant_modem] *from your system after these steps, it will be required to uninstall and patch the driver.*"

Note: if you find any problem, or want to make any change to the method, please write it in this thread, so we can have a proper final document.

---

### Post by nidzo732 on 2010-11-11
It works. I forgot how slow this thing was :mrgreen: .
One more question do i have to run hsfconfig when update the kernel.

---

### Post by Ganton on 2010-11-11
> **nidzo732 said:**
> One more question do i have to run hsfconfig when update the kernel.
I've looked for an answer, but I didn't find any information about it. In my case, I have been using Kubuntu Lucid (10.04) and upgrading the system (even its kernel) without executing hsfconfig and everything seemed to work right. 

When I updated from Lucid (10.04) to Maverick (10.10) the modem stopped working and I had to do those steps of the "how-to".

---

### Post by afrodeity on 2010-12-01
I've been having the same problem. 

Now tried the above hack and downloaded
[http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem_7.80.02.06full_k2.6.31_17_generic_ubuntu_i386.deb.zip](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem_7.80.02.06full_k2.6.31_17_generic_ubuntu_i386.deb.zip)

```

driver version 7.80.02.06full
(cd /lib/modules/2.6.36-020636rc7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.36-020636rc7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.36-020636rc7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.36-020636rc7-generic'
(cd /lib/modules/2.6.36-020636rc7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.36-020636rc7-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.36-020636rc7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.36-020636rc7-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.36-020636rc7-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.36-020636rc7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.36-020636rc7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.36-020636rc7-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320: warning: the frame size of 1028 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
  CC [M]  /usr/lib/hsfmodem/modules/osresour.o
/usr/lib/hsfmodem/modules/osresour.c: In function 'cnxthsf_7800206full_OsHookInterrupt':
/usr/lib/hsfmodem/modules/osresour.c:131: warning: the address of '__this_module' will always evaluate as 'true'
  CC [M]  /usr/lib/hsfmodem/modules/osstring.o
  CC [M]  /usr/lib/hsfmodem/modules/osmemory.o
  CC [M]  /usr/lib/hsfmodem/modules/osdiag.o
/usr/lib/hsfmodem/modules/osdiag.c:602: error: unknown field 'ioctl' specified in initializer
/usr/lib/hsfmodem/modules/osdiag.c:602: warning: initialization from incompatible pointer type
make[2]: *** [/usr/lib/hsfmodem/modules/osdiag.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.36-020636rc7-generic'
make: *** [all] Error 2
```

I guess this means I need to use the generic version?

---

### Post by Ganton on 2010-12-02
> I guess this means I need to use the generic version? 

I suppose it's so, you downloaded
[INDENT][http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem_7.80.02.06full_k2.6.31_17_generic_ubuntu_i386.deb.zip](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem_7.80.02.06full_k2.6.31_17_generic_ubuntu_i386.deb.zip)
[/INDENT]
and in the name of that file we find "2.6.31", which probably tells us that the file is only for the kernel "2.6.31".

However
[INDENT][http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz)[/INDENT]
does not have any kernel number in the name of the file, so I think it's more generic.

---

### Post by afrodeity on 2010-12-03
Generic one appears to work, :)

---

### Post by slaykristian on 2010-12-09
Hi all!!!

Only a question.

In maverick, do you think is necessary to install alsa-linuxant driver before hsf package?

Thanks!

---

### Post by Ganton on 2010-12-09
> In maverick, do you think is necessary to install alsa-linuxant driver before hsf package?
I didn't install the alsa-linuxant driver and everything seems to work ok. The other users of this thread did the same and didn't report any problem.

---

### Post by slaykristian on 2010-12-14
I followed your procedure, but when i do "sudo hsfconfig", this is the result:

```
driver version 7.68.00.09oem
(cd /lib/modules/2.6.33-29-realtime/build && make "CNXT_KERNELSRC=/lib/modules/2.6.33-29-realtime/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.33-29-realtime'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.33-29-realtime'
(cd /lib/modules/2.6.33-29-realtime/build && make "CNXT_KERNELSRC=/lib/modules/2.6.33-29-realtime/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.33-29-realtime'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.33-29-realtime'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.33-29-realtime/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.33-29-realtime/build && make "CNXT_KERNELSRC=/lib/modules/2.6.33-29-realtime/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.33-29-realtime'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320: warning: the frame size of 1028 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.33-29-realtime'
make: *** [all] Error 2
```

What can I do?!

Hellllllpppppp!!!!!!!!!!!!

---

### Post by Ganton on 2010-12-14
In the message you posted, it said:
> [...] /lib/modules/2.6.33-29 [...]
but that talks about an old Linux kernel.

If you execute
```
uname -a
```
what does it say?

---

### Post by slaykristian on 2010-12-14
> In the message you posted, it said:
Quote:
[...] /lib/modules/2.6.33-29 [...]
but that talks about an old Linux kernel.

If you execute
Code:

uname -a

what does it say? 

This is the answer:

> Linux chri-Inspiron-1520 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 20:14:20 UTC 2010 i686 GNU/Linux

---

### Post by Ganton on 2010-12-14
> Linux chri-Inspiron-1520 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 20:14:20 UTC 2010 i686 GNU/Linux 

Mmmm... it's really an older version of the Linux kernel, and seems to be a particular one. I have used the latest official version and it works, so maybe you can choose one of those paths:
- you can try to upgrade to the latest version of (K)ubuntu
- instead of using using [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz) you can try the previous version: [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.05full/hsfmodem-7.80.02.05full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.05full/hsfmodem-7.80.02.05full.tar.gz)  
- as they say in [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant):
"you can buy a Lucent or Intel (Smartlink, or other brand with Intel chipset) modem for less than 19.99 US." 
- [more options that we can imagine]

Anyway, if you choose a path, you can tell us how it went.

---

### Post by slaykristian on 2010-12-21
> **Ganton said:**
> Mmmm... it's really an older version of the Linux kernel, and seems to be a particular one. I have used the latest official version and it works, so maybe you can choose one of those paths:
- you can try to upgrade to the latest version of (K)ubuntu
- instead of using using [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz) you can try the previous version: [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.05full/hsfmodem-7.80.02.05full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.05full/hsfmodem-7.80.02.05full.tar.gz)  
- as they say in [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant):
"you can buy a Lucent or Intel (Smartlink, or other brand with Intel chipset) modem for less than 19.99 US." 
- [more options that we can imagine]

Anyway, if you choose a path, you can tell us how it went.

Yes, it's an old kernel version.
But, I experimented this:

I tried to re-install Lucid and ... Surprise! This procedure works fine with kernel 2.6.32-26, but you have to uninstall "pulseaudio" package. This is necessary because pulseaudio audio, when the system start, it uses the same codec necessary to hsfmodem packages to recognize modem.
A precisation... My modem is different from your. Mine is a built-in modem, not usb, my modem is integrated in my audio card (HDA Intel); for this, I need to install alsa-linuxant-driver package.


So, if I try a rt-kernel under Lucid, the result is the same of Maverick.. It doesn't function.

In conclusion...
I think that your previous procedure function only if you come from Lucid to Maverick.
And... We can apply it only if in /lib/modules/$(uname -r)/build/include/linux there are utsrelease.h and autoconf.h files or you're using a "generic" kernel (both in Lucid than in Maverick)!

Bye!

---

### Post by Ganton on 2010-12-23
I think we can clarify this:

[I]> I think that your previous procedure function only if you 
> come from Lucid to Maverick.[/I]
In one computer I tried, updating from Lucid to Maverick: it worked.
In another computer I tried, directly installing Maverick (not updating from Lucid): it worked.

---

### Post by TeamXlink on 2010-12-31
Ganton, I want to thank you for your tutorial on this.

I was using Ubuntu 8.04 and I had a hard drive failure, so I installed Ubuntu 10.10 on another hard drive. I tried to install the drivers the same way I did before, but it didn't work. I then did a Google search and the Ubuntu wiki page came up, it linked right to your tutorial, I followed your steps, and they worked perfectly!

Thank you!

---

### Post by slaykristian on 2011-01-11
Ganton,

do you think that is possible wich the driver isn't installable on rt kernel?

After my experience, I think that it works only with generic kernel.

Now, I'm using Lucid Lynx and your tutorial it works!
But in this case I'm using a generic kernel where autoconf.h and utsrelease.h are already installed in the "/lib/modules/$(uname -r)/build/include/linux" directory.

Thank you for all!!

Bye!

---

### Post by Ganton on 2011-01-15
> Do you think that is possible that the driver isn't installable on rt kernel?
I can't tell it for sure.

---

### Post by a.dehqan on 2011-03-04
In The Name Of God The compassionate merciful

Good day all ;
I-humble have done these steps > [http://ubuntuforums.org/showthread.php?p=10100007#post10100007](http://ubuntuforums.org/showthread.php?p=10100007#post10100007)

but this is hsfconfig output :
[http://pastebin.com/S4zXJYrx](http://pastebin.com/S4zXJYrx)

 so pppd says :Can't get terminal parameters: Input/output error
How to solve this problem ?

My os is :ubuntu 10.10 with no updates and is installed directly from CD.


Regards dehqan

---

### Post by Ganton on 2011-03-05
> My os is :ubuntu 10.10 with no updates and is installed directly from CD
Could you update the system first?, with something like
```
sudo apt-get update && sudo apt-get dist-upgrade
```

> I-humble have done these steps > [http://ubuntuforums.org/showthread.php?p=10100007#post10100007](http://ubuntuforums.org/showthread.php?p=10100007#post10100007)

but this is hsfconfig output :
[http://pastebin.com/S4zXJYrx](http://pastebin.com/S4zXJYrx)
Mmm... we see there 
> Conexant HSF softmodem driver, version 7.68.00.09oem
But that is an old version, maybe you had an error following the instructions and you have to follow them again from the start and tell us how it goes.

---

### Post by a.dehqan on 2011-03-06
In The Name Of Allah The compassionate merciful

> **Ganton said:**
> Could you update the system first?, with something like
```
sudo apt-get update && sudo apt-get dist-upgrade
```


Hello and thanks for reply
no in fact my internet speed is low and con not update ..

> **Ganton said:**
> 
Mmm... we see there 

But that is an old version, maybe you had an error following the instructions and you have to follow them again from the start and tell us how it goes.
no there is no error and result is the same .and this 
```
Conexant HSF softmodem driver, version 7.68.00.09oem 
```
is exactly  result of your instructions .

of course my laptop modem is internal modem and is not usb modem ,maybe this is why hsfconfig says :

> Warning: no device detected by hsf driver - HDA modems may require reboot

Note: HDA support not compiled in the driver

and it seems your instructions are for usb modem only ?
What instruction is usefull for internal hsfmodem in ubuntu 10.10 ?

Regards dehqan

---

### Post by shizeon on 2011-03-06
Ganton,  Thanks for the guide!  I now have a **working** internal PCI modem card using the Conexant chipset.

```
$ lspci  | grep Conexant
05:01.0 Communication controller: Conexant Systems, Inc. SoftV92 SpeakerPhone SoftRing Modem with SmartSP (rev 01)
```

I am also running 64-bit Ubuntu 10.10.  Using your guide, with a few changes, I was able to get this working.  I primarily use this for fax purposes, so I haven't tested the connection speeds, but I have been able to send and receive a couple different faxes so it is at least working okay there.

I followed your instructions to the tee but made the following changes: 

[LIST=1]
[*]Replace the string 'hsfmodem-7.68.00.09oem' with 'hsfmodem-7.68.00.09x86_64oem'
[*]Replace the string 'hsfmodem-7.80.02.06full.tar.gz' with 'hsfmodem-7.80.02.06x86_64full'
[/LIST]

Both the dell site and the linuxant site had x64 tar balls.  I used the hsfmodem-7.80.02.05-DiacoEdition just as is. 

After running hsfconfig I have a modem again.

```
[84658.840646] hsfpcibasic2 0000:05:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[84659.195886] ttySHSF0 at I/O 0xbf00 (irq = 19) is a Conexant HSF softmodem (PCI-14f1:2f30-14f1:2051)
[84659.241554] usbcore: registered new interface driver hsfusbcd2
```

Thanks for the help!

---

### Post by a.dehqan on 2011-03-07
In The Name Of Allah The compassionate merciful

Hello 
Any opinion about my problem ?

Regards dehqan

---

### Post by Ganton on 2011-03-11
> Any opinion about my problem ?
Like shizeon wrote, you could try to execute
```
lspci  | grep Conexant
```
and tell us the results.

---

### Post by a.dehqan on 2011-03-12
> **Ganton said:**
> Like shizeon wrote, you could try to execute
```
lspci  | grep Conexant
```
and tell us the results.
In The Name Of Allah The compassionate merciful

Hello;
Thank you

Lspci does not show anything ,maybe because of that  my modem is integrated in my audio card.
This scanmodem result :
[http://pastebin.com/fEQSMXhz](http://pastebin.com/fEQSMXhz)
That telegent is related to my tv dongel driver.
I-humble also removed pulsaudio package regarding to [this post ]("http://ubuntuforums.org/showpost.php?p=10263688&postcount=18") but now ubuntu has not sound.

And this is result of installing alsa-driver-linuxant_1.0.23.1_all.deb > [http://pastebin.com/qJfbczxB](http://pastebin.com/qJfbczxB)


..but my modem works in ubuntu 9.04 with dell driver (full speed) and some other kernels ..


Regards dehqan

---

### Post by Fentanyl on 2011-04-02
> **shizeon said:**
> Ganton,  Thanks for the guide!  I now have a **working** internal PCI modem card using the Conexant chipset.

```
$ lspci  | grep Conexant
05:01.0 Communication controller: Conexant Systems, Inc. SoftV92 SpeakerPhone SoftRing Modem with SmartSP (rev 01)
```I am also running 64-bit Ubuntu 10.10.  Using your guide, with a few changes, I was able to get this working.  I primarily use this for fax purposes, so I haven't tested the connection speeds, but I have been able to send and receive a couple different faxes so it is at least working okay there.

I followed your instructions to the tee but made the following changes: 

[LIST=1]
[*]Replace the string 'hsfmodem-7.68.00.09oem' with 'hsfmodem-7.68.00.09x86_64oem'
[*]Replace the string 'hsfmodem-7.80.02.06full.tar.gz' with 'hsfmodem-7.80.02.06x86_64full'
[/LIST]

Both the dell site and the linuxant site had x64 tar balls.  I used the hsfmodem-7.80.02.05-DiacoEdition just as is. 

After running hsfconfig I have a modem again.

```
[84658.840646] hsfpcibasic2 0000:05:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[84659.195886] ttySHSF0 at I/O 0xbf00 (irq = 19) is a Conexant HSF softmodem (PCI-14f1:2f30-14f1:2051)
[84659.241554] usbcore: registered new interface driver hsfusbcd2
```Thanks for the help!

I have a conexant pci modem, running on ubuntu 11.04beta1 x64
I did exactly what you did and this was the response

```

ERROR: Module build failed!
Please examine the log file "/etc/hsfmodem/log/buildlog-20110402173304.txt" to determine why.

```

Then, i opened that file:


```

driver version 7.68.00.09x86_64oem
(cd /lib/modules/2.6.38-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
(cd /lib/modules/2.6.38-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-7-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.38-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-7-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsInit':
/usr/lib/hsfmodem/modules/osservices.c:1287:80: warning: format '%d' expects type 'int', but argument 2 has type 'long unsigned int'
/usr/lib/hsfmodem/modules/osservices.c:1287:80: warning: format '%d' expects type 'int', but argument 3 has type 'long unsigned int'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408:8: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
make: *** [all] Error 2

```

Can you guys please help me? :(
I really need a fax on my ubuntu...
Thanks a lot in advance...

---

### Post by L_V on 2011-04-07
Exactly same problem with hsfmodem:

```
/usr/lib/hsfmodem/modules/osnvm.c:408:8: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
make: *** [all] Error 2
```

Which is the latest known kernel release hsfmodem is supposed to work with ?

---

### Post by backu on 2011-05-10
Was having the same issues with 'MUTEX' problems, and a look around at blogs and other things told me to change DECLARE_MUTEX in the file to DEFINE_SEMAPHORE, which appears to have worked, but now I get an "/usr/lib/hsfmodem/modules/osdiag.c:602:5: error: unknown field 'ioctl' specified in initializer"

Anyone out there savvy enough already with Natty to understand how the hell to install Conexant HSF drivers?:confused:

---

### Post by backu on 2011-05-10
Okay, not sure exactly how I found it cause it never came up under any of my other searches pertaining to HSFModem, but there is a patch file out on OpenMAMBA that basicly showed the same thing I did, change the DECLARE_MUTEX to DEFINE_SEMAPHORE (2 files), and replace .ioctl with .compat_ioctl. After doing those 2 things, HSFConfig ran and built the driver just fine on Natty 11.04

---

### Post by pi.boy.travis on 2011-05-15
THANK YOU ALL SO MUCH! Finally got this working! w00t!

---

### Post by pi.boy.travis on 2011-05-15
Well, it's almost working. When I run hsfconfig it spits this out:

Warning: no device detected by hsf driver - HDA modems may require reboot

Note: HDA support not compiled in the driver


I've installed the alsa-driver-linuxant-1.0.23.1_all.deb . I'm not sure where to go from here. . .

---

### Post by pi.boy.travis on 2011-05-15
Yikes, looks like this has broken all sound output on my system too. . .

---

### Post by Ganton on 2011-06-13
Note: This particular thread was marked as "solved" because it was for Ubuntu 10.10 (Maverick Meerkat).

To avoid mixing versions, if someone is using another version, like 11.04 (Natty Narwhal), he can see [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant) for an appropriate thread for his operating system. 

Thanks!

---

