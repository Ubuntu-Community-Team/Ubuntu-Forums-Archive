---
title: "how to build driver tarball?"
date: 2010-04-04
forum: General Help
---

### Post by teh'p3nsi0n3r on 2010-04-04
my dads decided to try out ubuntu on his pc, so far everythings up and running smoothly. i am trying to get the video capture card working with tvtime.


I have ran "lspci" in the terminal which has detected the following.


00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]
01:00.1 Display controller: ATI Technologies Inc RV530LE [Radeon X1650 PRO] (Secondary)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
03:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:05.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:05.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

it has detected the "03:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)" the card we are trying to get up and running. 
TV Time is not detecting the video being fed through from the cable like it does in windows. So it made sense i would have to possible install the driver. After searching these forums and google, I found a link to the following site. 

[http://linux.bytesex.org/v4l2/build.html](http://linux.bytesex.org/v4l2/build.html)

This shows how to build the drivers. And this is where I've ran in to a few issues.


"building the driver tarballs

This is pretty simple:

mkdir <workdir>
cd <workdir>
tar xzf /path/to/driver-version.tar.gz
cd driver-version
make KDIR=/path/to/kernel/source/tree
make install"

I get as far as "make KDIR=/path/to/kernel/source/tree" and got lost, i am running ubuntu 9.10. What do i put where =KDIR is?. 

any help appreciated. :)

---

### Post by teh'p3nsi0n3r on 2010-04-04
anyone?

---

### Post by Oldskool Slacker on 2010-04-04
> **teh'p3nsi0n3r said:**
> 

I get as far as "make KDIR=/path/to/kernel/source/tree" and got lost,.... What do i put where =KDIR is?. 

any help appreciated. :)

The next line on the page you linked says:

> Usually the correct path to the kernel source tree is picked automagically, you only need the KDIR argument for make if this doesn't work for some reason.

Personally, I have never used "KDIR".  Just type "make", it should work.

---

### Post by teh'p3nsi0n3r on 2010-04-04
hi thanks for your reply. i read on a site that tvtime/recent versions of linux should already be compatible with this card, so im not sure if it needs this driver. but i ran "make" anyway and here is what i got.


make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/ray/capture/saa7134-0.2.12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/ray/capture/saa7134-0.2.12/video-buf.o
In file included from /home/ray/capture/saa7134-0.2.12/media/video-buf.h:19,
                 from /home/ray/capture/saa7134-0.2.12/video-buf.c:33:
/home/ray/capture/saa7134-0.2.12/linux/videodev.h:68: error: field 'class_dev' has incomplete type
/home/ray/capture/saa7134-0.2.12/linux/videodev.h:87: warning: 'struct class_device_attribute' declared inside parameter list
/home/ray/capture/saa7134-0.2.12/linux/videodev.h:87: warning: its scope is only this definition or declaration, which is probably not what you want
/home/ray/capture/saa7134-0.2.12/linux/videodev.h: In function 'video_device_create_file':
/home/ray/capture/saa7134-0.2.12/linux/videodev.h:89: error: implicit declaration of function 'class_device_create_file'
/home/ray/capture/saa7134-0.2.12/linux/videodev.h: At top level:
/home/ray/capture/saa7134-0.2.12/linux/videodev.h:93: warning: 'struct class_device_attribute' declared inside parameter list
/home/ray/capture/saa7134-0.2.12/linux/videodev.h: In function 'video_device_remove_file':
/home/ray/capture/saa7134-0.2.12/linux/videodev.h:95: error: implicit declaration of function 'class_device_remove_file'
/home/ray/capture/saa7134-0.2.12/video-buf.c: At top level:
/home/ray/capture/saa7134-0.2.12/video-buf.c:46: error: expected ')' before string constant
/home/ray/capture/saa7134-0.2.12/video-buf.c: In function 'videobuf_vmalloc_to_sg':
/home/ray/capture/saa7134-0.2.12/video-buf.c:68: error: 'struct scatterlist' has no member named 'page'
/home/ray/capture/saa7134-0.2.12/video-buf.c: In function 'videobuf_pages_to_sg':
/home/ray/capture/saa7134-0.2.12/video-buf.c:96: error: 'struct scatterlist' has no member named 'page'
/home/ray/capture/saa7134-0.2.12/video-buf.c:104: error: 'struct scatterlist' has no member named 'page'
/home/ray/capture/saa7134-0.2.12/video-buf.c: In function 'videobuf_vm_nopage':
/home/ray/capture/saa7134-0.2.12/video-buf.c:1099: error: 'NOPAGE_SIGBUS' undeclared (first use in this function)
/home/ray/capture/saa7134-0.2.12/video-buf.c:1099: error: (Each undeclared identifier is reported only once
/home/ray/capture/saa7134-0.2.12/video-buf.c:1099: error: for each function it appears in.)
/home/ray/capture/saa7134-0.2.12/video-buf.c:1102: error: 'NOPAGE_OOM' undeclared (first use in this function)
/home/ray/capture/saa7134-0.2.12/video-buf.c: At top level:
/home/ray/capture/saa7134-0.2.12/video-buf.c:1119: error: unknown field 'nopage' specified in initializer
/home/ray/capture/saa7134-0.2.12/video-buf.c:1119: warning: initialization from incompatible pointer type
make[2]: *** [/home/ray/capture/saa7134-0.2.12/video-buf.o] Error 1
make[1]: *** [_module_/home/ray/capture/saa7134-0.2.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [default] Error 2


any ideas?

---

