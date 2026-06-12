---
title: "Trouble compiling driver for Sierra 306 CDMA modem"
date: 2009-12-22
forum: General Help
---

### Post by cecure on 2009-12-22
Hello I am trying to compile the drivers for the Sierra 306 wireless modem based on the instructions found at [http://sierrawireless.custhelp.com/app/answers/detail/a_id/641/kw/sierra%20306%20linux/r_id/166]("http://sierrawireless.custhelp.com/app/answers/detail/a_id/641/kw/sierra%20306%20linux/r_id/166").

I have been able to compile them on my x86 but am having trouble on my laptop.  I am running Jaunty on a Athlon 64.  

The compile problems seem to be located within the sierra_net.c file.  I am wondering do I need to change something in the makefile because I am on an amd?

Here is my compile output:
```
Compiling  sierra.c sierra_net.c
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-17-generic'
  CC [M]  /home/donna/src/sierra306/sierra_net.o
/home/donna/src/sierra306/sierra_net.c: In function ‘build_ip’:
/home/donna/src/sierra306/sierra_net.c:502: warning: cast from pointer to integer of different size
/home/donna/src/sierra306/sierra_net.c: In function ‘sierra_net_parse_lsi’:
/home/donna/src/sierra306/sierra_net.c:828: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘long unsigned int’
/home/donna/src/sierra306/sierra_net.c: At top level:
/home/donna/src/sierra306/sierra_net.c:1406: warning: cast from pointer to integer of different size
/home/donna/src/sierra306/sierra_net.c:1406: error: initializer element is not constant
/home/donna/src/sierra306/sierra_net.c:1406: error: (near initialization for ‘sierra_net_info_68A3.data’)
make[2]: *** [/home/donna/src/sierra306/sierra_net.o] Error 1
make[1]: *** [_module_/home/donna/src/sierra306] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-17-generic'
make: *** [default] Error 2

```

I would appreciate any help at all :)

---

### Post by cecure on 2009-12-22
I want to try to compile this with the gcc -m32 option, to see if it will compile in 32 bit.  I am unfamiliar with the makefile format and have been unable to figure it out using Google.  How can I add compiler options to this makefile?

```
# Copyright Sierra Wireless 2009
#
# Makefile to install the Sierra modules/drivers.
#
# Dependencies: 
#      sierra depends on usbserial (serial driver)
#      sierra_net depends on usbnet (network driver) 
#
# Assumptions:
# 	This makefile assumes that kernel modules are installed in 
#	      /lib/modules/'uname -r'/.
#	Should the assumption be incorrect, please use:
#	    make MODULE_ROOT="/path/to/modules/for/your/kernel"
#	to override assumed path
#
# Serial driver is required, built all the time, the network driver is optional
# and may be removed from the build simply by renaming the sierra_net.c file or
# deleting it completely.

#
# sierra.c is required source, sierra_net.c is optional source
# therefore we build obj-m below conditionaly, based on files present on disk
srcs := sierra.c $(wildcard sierra_net.c)
obj-m := $(srcs:%.c=%.o)

MODULE_ROOT:= /lib/modules/$(shell uname -r)
BUILDDIR   := $(MODULE_ROOT)/build
USBDIR     := $(MODULE_ROOT)/kernel/drivers/usb/serial
NETDIR     := $(MODULE_ROOT)/kernel/drivers/net/usb
PWD        := $(shell pwd)

override install_targets := $(srcs:%.c=install_%)

#-------------------- Rules ------------------

all: default

default:
	@echo "-----------------------------------------------------"
	@echo "Compiling " $(srcs)
	@$(MAKE) -C $(BUILDDIR) SUBDIRS=$(PWD) "obj-m=$(obj-m)" modules
	@echo "-----------------------------------------------------"

.PHONY: default install all clean help $(install_targets)

install_sierra:
	@install -m 644 sierra.ko $(USBDIR)
	@depmod -a
	@modprobe -r sierra
	@modprobe sierra

install_sierra_net:
	@install -b -m 644 sierra_net.ko $(NETDIR)
	@depmod -a
	@modprobe -r sierra_net
	@modprobe sierra_net

# install depends on the installation of current driver set 
install: $(install_targets)

debug:
	@echo
	@echo "srcs="$(srcs)
	@echo "obj-m="$(obj-m)
	@echo "MODULE_ROOT="$(MODULE_ROOT)
	@echo "PWD="$(PWD)
	@echo "install targets: " $(install_targets)
	@echo

help:
	@echo 
	@echo Use: make [target]
	@echo Note:make without a target is the same as \'make default\'
	@echo
	@echo Available targets:
	@echo " default - build drivers in this directory" 
	@echo " all - same as default" 
	@echo " install - install previously built drivers (requires su privileges)" 
	@echo " install_sierra_net - install network/ethernet driver only (su privileges required)"
	@echo " install_sierra - install serial driver only (su privileges required)"
	@echo " help - this help"
	@echo

clean:
	-@rm -rf *.o *.ko sierra*.mod.c Module.symvers .sierra* .tmp_versions modules.order


# Copyright Sierra Wireless 2009

```

Thanks :)

---

### Post by FireYello on 2009-12-23
Hi

Here is a patch you might try; I created it by inspecting the code and the underlying data structures to see if my changes would be correct and they seem to be. Unfortunately I do not have a 64 bit machine available to test that it actually works; NOTE: also, just because the (may) compile after these changes doesn't mean there are other more nasty kinds of problems that arise because of the designer's original assumption that the driver would be running on a 32 bit machine. 

The best you can do is try it and see - unless someone else out there with a 64 bit machine can assist. To install this patch, copy the following text into a file in the same directory as your sierra_net.c driver. Then, open a terminal window, navigate to that directory and run the following command:

patch -p1 < sierra_net.patch <-  [edit] This assumes you save the patch below in a file called sierra_net.patch

Then re-run the make instructions you tried before. If that doesn't compile, then please repost the error and I'll see if I can fix it for you. If it compiles but doesn't run, you'd be better off asking Sierra Wireless to port it to 64 bits for you. 

Cheers

FY

--- ../kernel-2.6.28/sierra_net.c    2009-09-28 17:11:58.000000000 -0700
+++ sierra_net.c    2009-12-23 10:01:10.000000000 -0800
@@ -499,7 +499,7 @@ static void build_ip(struct sk_buff *in,
 
     iphdr->version = 4;
     iphdr->ihl = sizeof( *iphdr ) / 4;
-    iphdr->id = (u32)iphdr;
+    iphdr->id = (u16) iphdr;
     iphdr->ttl = 1;
     iphdr->protocol = IPPROTO_UDP;
     iphdr->saddr = saddr;
@@ -825,7 +825,7 @@ static int sierra_net_parse_lsi(struct u
     lsi_umts_t *lsi = (lsi_umts_t*)data;
 
     if (lsi->length != cpu_to_be16(SIERRA_NET_LSI_UMTS_STATUS_LEN)) {
-        deverr(dev, "%s: LSI_UMTS_STATUS_LEN %d, expected %d",
+        deverr(dev, "%s: LSI_UMTS_STATUS_LEN %d, expected %ld",
                 __FUNCTION__, be16_to_cpu(lsi->length),
                 SIERRA_NET_LSI_UMTS_STATUS_LEN);
         return -1;
@@ -1403,7 +1403,7 @@ static const struct driver_info sierra_n
     .status = sierra_net_status,
     .rx_fixup = sierra_net_rx_fixup,
     .tx_fixup = sierra_net_tx_fixup,
-    .data = (unsigned int)&sierra_net_info_data_68A3,
+    .data = (int) ( (void *)&sierra_net_info_data_68A3),
 };

---

### Post by ivs_q on 2010-01-01
Hi,

Migrating from Vista, I have recently installed Karmic amd64 on my laptop, and would like to use my Sierra 306 wireless modem. Would the above guidelines work for Karmic too?

Many thanks.

---

### Post by FireYello on 2010-01-11
> **ivs_q said:**
> Hi,

Migrating from Vista, I have recently installed Karmic amd64 on my laptop, and would like to use my Sierra 306 wireless modem. Would the above guidelines work for Karmic too?

Many thanks.

Well in principle it should work, but you won't know until you try. Same warning tho, if it compiles there's no guarantee that there aren't some flaws in the logic lurking around. But// I don't think you will damage anything if you try it and it crashes. The worst that should happen is the kernel may crash and you will need to reboot. In that case, don't plug your modem in again until you have removed the driver from the machine so it doesn't crash again. 

YMMV. 

Regards, 

FY

---

