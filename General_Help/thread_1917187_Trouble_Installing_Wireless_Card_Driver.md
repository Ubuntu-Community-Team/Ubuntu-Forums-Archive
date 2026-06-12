---
title: "Trouble Installing Wireless Card Driver"
date: 2012-01-29
forum: General Help
---

### Post by JulienZ on 2012-01-29
Hello Everyone, first post on these forums, or any Ubuntu help site for that matter. I'll try to be as precise as possible in my explanation to facilitate clear understanding of my problem.

Me : New Ubuntu user ( just about a week now ), currently dual booting Ubuntu 11.1 Oneiric alongside Windows 7 on a newly build PC. First time user of any Linux software 

What I'm trying to do : I'm trying to get my wireless card to work in Ubuntu

Specifics : Wireless Card : Tenda W322P+ V2.0 ( Wireless PCI Adapter )
                  OS                  : DISTRIB_ID=Ubuntu
                                           DISTRIB_RELEASE=11.10
                                           DISTRIB_CODENAME=oneiric
                                           DISTRIB_DESCRIPTION="Ubuntu 11.10"

My Problem : The card is physically installed in the machine, and works when in Windows 7. The problem, therefore is that I can't get the driver to work for Linux. I have the installation CD, but as a very new user to Ubuntu, some of the driver installation instructions aren't clear to me. To be clear, the CD comes with a README file that asks me to make changes to 2 different files, one called "config.mk" and one "Makefile". Some of these changes are pretty straightforward but others really throw me for a loop. I'll post exerts to show you exactly what i mean.

Build Instructions:  
====================

1> $tar -xvzf RT3572_Linux_STA_x.x.x.x.tgz
    go to "./RT3572_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

These instructions are from the README file. At this point, I've copied the Linux folder that was on the cd in a /usr/local/src folder that i created. Then when I attempt to  "make clean" then "make" ( in terminal from within the directory of the folder in question ) I get a bunch of errors. Here are a few of them :

ER **’
/usr/local/src/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/usr/local/src/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/usr/local/src/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/usr/local/src/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’

I suspect these errors are due to the bad configuration of the files mentionned in the readme. However I do not currently understand how to follow instructions 2 and 3. Can someone clarify what is meant by :
-GCC and LD
-compiler flags CFLAGS
-kernel source include file path LINUX_SRC


NOTE : I would post the files referenced here ( the "config.mk" and "Makefile" ) so you guys can help me make the changes in the right places too, but these are long files. Anyone know how make them appear in a small scrollable textbox within a forum post ?

Anyway Thanks for the help, and aside from the slightly steep learning curve, I am loving Ubuntu so far !

Julien

---

