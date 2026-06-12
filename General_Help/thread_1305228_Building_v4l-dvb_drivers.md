---
title: "Building v4l-dvb drivers"
date: 2009-10-29
forum: General Help
---

### Post by scweston on 2009-10-29
Hi,

I hope my question isn't too specific for the 'general help' section of this forum, but I'm having problems building and installing the v4l-dvb drivers I need to get my tv tuner card working properly.

I've done a fresh install in Karmic using the recently released final version and followed the guide here  [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Everything seems to work smoothly until I get the errors below about 3minutes in to te building process: -

```

  CC [M]  /home/stephen/v4l-dvb/v4l/em28xx-audio.o
  CC [M]  /home/stephen/v4l-dvb/v4l/em28xx-video.o
  CC [M]  /home/stephen/v4l-dvb/v4l/em28xx-i2c.o
  CC [M]  /home/stephen/v4l-dvb/v4l/em28xx-cards.o
  CC [M]  /home/stephen/v4l-dvb/v4l/em28xx-core.o
  CC [M]  /home/stephen/v4l-dvb/v4l/em28xx-input.o
  CC [M]  /home/stephen/v4l-dvb/v4l/em28xx-vbi.o
  CC [M]  /home/stephen/v4l-dvb/v4l/et61x251_core.o
/home/stephen/v4l-dvb/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/stephen/v4l-dvb/v4l/et61x251_core.c:2493: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/stephen/v4l-dvb/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/stephen/v4l-dvb/v4l/firedtv-avc.o
  CC [M]  /home/stephen/v4l-dvb/v4l/firedtv-ci.o
  CC [M]  /home/stephen/v4l-dvb/v4l/firedtv-dvb.o
  CC [M]  /home/stephen/v4l-dvb/v4l/firedtv-fe.o
  CC [M]  /home/stephen/v4l-dvb/v4l/firedtv-1394.o
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:37: warning: 'struct hpsb_iso' declared inside parameter list
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:37: warning: its scope is only this definition or declaration, which is probably not what you want
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:53: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:54: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:61: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:62: error: implicit declaration of function 'dma_region_i'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:62: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:62: error: expected expression before 'unsigned'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:63: warning: assignment makes pointer from integer without a cast
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:82: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:87: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:87: warning: type defaults to 'int' in declaration of '__mptr'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:87: warning: initialization from incompatible pointer type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:87: error: invalid use of undefined type 'struct unit_directory'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:92: error: implicit declaration of function 'hpsb_node_lock'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:92: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:92: error: (Each undeclared identifier is reported only once
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:92: error: for each function it appears in.)
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:93: error: 'quadlet_t' undeclared (first use in this function)
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:93: error: expected ')' before 'arg'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_read'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:103: error: implicit declaration of function 'hpsb_node_write'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:114: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:114: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:116: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:118: warning: assignment makes pointer from integer without a cast
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:125: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:128: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:139: error: implicit declaration of function 'hpsb_iso_stop'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:154: warning: 'struct hpsb_host' declared inside parameter list
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:167: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:168: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:182: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:182: warning: type defaults to 'int' in declaration of '__mptr'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:182: warning: initialization from incompatible pointer type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:182: error: invalid use of undefined type 'struct unit_directory'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:187: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:187: error: 'quadlet_t' undeclared (first use in this function)
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:188: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:188: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:188: warning: assignment makes pointer from integer without a cast
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:243: warning: 'struct unit_directory' declared inside parameter list
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:245: error: dereferencing pointer to incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:253: error: variable 'fdtv_driver' has initializer but incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:254: error: unknown field 'name' specified in initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:254: warning: excess elements in struct initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:254: warning: (near initialization for 'fdtv_driver')
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:255: error: unknown field 'update' specified in initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:255: warning: excess elements in struct initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:255: warning: (near initialization for 'fdtv_driver')
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:256: error: unknown field 'driver' specified in initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:256: error: extra brace group at end of initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:256: error: (near initialization for 'fdtv_driver')
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:259: warning: excess elements in struct initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:259: warning: (near initialization for 'fdtv_driver')
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:262: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_highlevel')
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:264: error: unknown field 'fcp_request' specified in initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_highlevel')
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:271: error: implicit declaration of function 'hpsb_register_highlevel'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:272: error: invalid use of undefined type 'struct hpsb_protocol_driver'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:273: error: implicit declaration of function 'hpsb_register_protocol'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:276: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/stephen/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/stephen/v4l-dvb/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/stephen/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/stephen/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/stephen/v4l-dvb/v4l'
make: *** [all] Error 2
stephen@stephen-desktop:~/v4l-dvb$ 

```

I'm not a linux expert and do most things by following How-To guides, but can find nothing to help me here. Anybody able to help?

If you need any more details to enable you to assist me the please let me know.

Stephen

---

### Post by gefenm11 on 2009-10-30
in the v4l folder, open the **.config** file,
find the line
```
CONFIG_DVB_FIREDTV=m
```
and change it to
```
CONFIG_DVB_FIREDTV=n

```

---

### Post by scweston on 2009-10-30
Thanks gefenm11,

Your instructions worked perfectly. Now have managed to build and install the v4l-dvb driver.

Much appreciated
Stephen

---

### Post by spleblem on 2009-11-17
sorry, please delete post

---

### Post by ahti000 on 2009-11-18
cant find any .config file with that line actually. What might be wrong

---

### Post by scweston on 2009-11-18
> **ahti000 said:**
> cant find any .config file with that line actually. What might be wrong

Hi ahti000

Initially I had trouble finding it too! If I remember correctly I couldn't find the .config file after I had created the v4l-dvb folder with the following command: -

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

However, after trying to build the drivers with the 'make' command (and failing) the .config file appeared in v4l folder inside the v4l-dvb directory. I then edited that file and just ran the 'make' command again, which then seemed to work.

Hope this helps!  I imagine the as part of the make command it creates a default .config file.

Also, remember the .config file is a hidden file so if your looking for it in a file manager you'll need to select 'view hidden files' somewhere in the options.

---

### Post by amin-v on 2009-12-03
> **gefenm11 said:**
> in the v4l folder, open the **.config** file,
find the line
```
CONFIG_DVB_FIREDTV=m
```and change it to
```
CONFIG_DVB_FIREDTV=n

```


Thanks  gefenm11 
It worked great with me

I found the file **.config** in  **v4l-dvb/v4l**

also you could generate a new one with this command 
**make config**

---

### Post by markackerman8@gmail.com on 2010-03-26
Awesome working for me too, thanks guys, this may be a turning point for my linux experience!

---

### Post by Dark_Jack on 2010-04-23
I have problems with:

**Make:**

```
  CC      /home/antonio/v4l-dvb/v4l/zr364xx.mod.o
  LD [M]  /home/antonio/v4l-dvb/v4l/zr364xx.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
./scripts/rmmod.pl check
found 341 modules
make[1]: se sale del directorio `/home/antonio/v4l-dvb/v4l'
antonio@antonio-desktop:~/v4l-dvb$
```
[B]
Make install:[/B]

```
    video/zc0301/: zc0301.ko 
    video/au0828/: au0828.ko 
/sbin/depmod -a 2.6.32-21-generic 
make -C firmware install
make[2]: Entering directory `/home/antonio/v4l-dvb/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/antonio/v4l-dvb/v4l/firmware'
make[1]: se sale del directorio `/home/antonio/v4l-dvb/v4l'
antonio@antonio-desktop:~/v4l-dvb$
```

---

### Post by Dark_Jack on 2010-04-25
does not work, can someone help me?

---

### Post by jmols on 2010-08-21
> **Dark_Jack said:**
> I have problems with:

**Make:**

```
  CC      /home/antonio/v4l-dvb/v4l/zr364xx.mod.o
  LD [M]  /home/antonio/v4l-dvb/v4l/zr364xx.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
./scripts/rmmod.pl check
found 341 modules
make[1]: se sale del directorio `/home/antonio/v4l-dvb/v4l'
antonio@antonio-desktop:~/v4l-dvb$
```[B]
Make install:[/B]

```
    video/zc0301/: zc0301.ko 
    video/au0828/: au0828.ko 
/sbin/depmod -a 2.6.32-21-generic 
make -C firmware install
make[2]: Entering directory `/home/antonio/v4l-dvb/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/antonio/v4l-dvb/v4l/firmware'
make[1]: se sale del directorio `/home/antonio/v4l-dvb/v4l'
antonio@antonio-desktop:~/v4l-dvb$
```

I had the same error on Ubuntu 10.04, but I was able to solve it by runing "sudo make install"

---

### Post by Nausser on 2011-04-18
This worked out for me. Jut have to watch that FireDTV option in the .config file as explained.

I do have to re-compile/install this each time I have a kernel update though. Very frustrating. If anyone knows how to do this so it stays updated to each kernel install, that would be fantastic!

---

### Post by calande on 2011-05-07
Hello,

I'm now unable to compile v4l-dvb on natty :(
Here's the output:

```
charles@charles-desktop:~/v4l-dvb$ make
make -C /home/charles/v4l-dvb/v4l 
make[1]: Entering directory `/home/charles/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.38

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

WARNING: You're using an obsolete driver! You shouldn't be using it!
	 If you want anything new, you can use:
		http://git.linuxtv.org/media_build.git.
	 The tree is still here just to preserve the development history.
	 You've been warned.
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/charles/v4l-dvb/v4l'
make[1]: Entering directory `/home/charles/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.38-8-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/charles/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/charles/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/charles/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/charles/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.38-8-generic/build
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/charles/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/charles/v4l-dvb/v4l/tuner-xc2028.o
  CC [M]  /home/charles/v4l-dvb/v4l/tuner-simple.o
  CC [M]  /home/charles/v4l-dvb/v4l/tuner-types.o
  CC [M]  /home/charles/v4l-dvb/v4l/mt20xx.o
  CC [M]  /home/charles/v4l-dvb/v4l/tda8290.o
  CC [M]  /home/charles/v4l-dvb/v4l/tea5767.o
  CC [M]  /home/charles/v4l-dvb/v4l/tea5761.o
  CC [M]  /home/charles/v4l-dvb/v4l/tda9887.o
  CC [M]  /home/charles/v4l-dvb/v4l/tda827x.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-core.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-i2c.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-cards.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-dvb.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-video.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-vbi.o
  CC [M]  /home/charles/v4l-dvb/v4l/au8522_dig.o
  CC [M]  /home/charles/v4l-dvb/v4l/au8522_decoder.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-i2c.o
/home/charles/v4l-dvb/v4l/flexcop-i2c.c: In function 'flexcop_i2c_init':
/home/charles/v4l-dvb/v4l/flexcop-i2c.c:253:39: error: 'I2C_CLASS_TV_DIGITAL' undeclared (first use in this function)
/home/charles/v4l-dvb/v4l/flexcop-i2c.c:253:39: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/charles/v4l-dvb/v4l/flexcop-i2c.o] Error 1
make[2]: *** [_module_/home/charles/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/charles/v4l-dvb/v4l'
make: *** [all] Error 2
charles@charles-desktop:~/v4l-dvb$
```

Could you help me please?
Thanks,

---

### Post by ultimbro on 2011-05-14
> **calande said:**
> Hello,

I'm now unable to compile v4l-dvb on natty :(
Here's the output:

```
charles@charles-desktop:~/v4l-dvb$ make
make -C /home/charles/v4l-dvb/v4l 
make[1]: Entering directory `/home/charles/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.38

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

WARNING: You're using an obsolete driver! You shouldn't be using it!
	 If you want anything new, you can use:
		http://git.linuxtv.org/media_build.git.
	 The tree is still here just to preserve the development history.
	 You've been warned.
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/charles/v4l-dvb/v4l'
make[1]: Entering directory `/home/charles/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.38-8-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/charles/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/charles/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/charles/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/charles/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.38-8-generic/build
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/charles/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/charles/v4l-dvb/v4l/tuner-xc2028.o
  CC [M]  /home/charles/v4l-dvb/v4l/tuner-simple.o
  CC [M]  /home/charles/v4l-dvb/v4l/tuner-types.o
  CC [M]  /home/charles/v4l-dvb/v4l/mt20xx.o
  CC [M]  /home/charles/v4l-dvb/v4l/tda8290.o
  CC [M]  /home/charles/v4l-dvb/v4l/tea5767.o
  CC [M]  /home/charles/v4l-dvb/v4l/tea5761.o
  CC [M]  /home/charles/v4l-dvb/v4l/tda9887.o
  CC [M]  /home/charles/v4l-dvb/v4l/tda827x.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-core.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-i2c.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-cards.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-dvb.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-video.o
  CC [M]  /home/charles/v4l-dvb/v4l/au0828-vbi.o
  CC [M]  /home/charles/v4l-dvb/v4l/au8522_dig.o
  CC [M]  /home/charles/v4l-dvb/v4l/au8522_decoder.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /home/charles/v4l-dvb/v4l/flexcop-i2c.o
/home/charles/v4l-dvb/v4l/flexcop-i2c.c: In function 'flexcop_i2c_init':
/home/charles/v4l-dvb/v4l/flexcop-i2c.c:253:39: error: 'I2C_CLASS_TV_DIGITAL' undeclared (first use in this function)
/home/charles/v4l-dvb/v4l/flexcop-i2c.c:253:39: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/charles/v4l-dvb/v4l/flexcop-i2c.o] Error 1
make[2]: *** [_module_/home/charles/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/charles/v4l-dvb/v4l'
make: *** [all] Error 2
charles@charles-desktop:~/v4l-dvb$
```

Could you help me please?
Thanks,

I got the same error .. don't know what to do.. any help someone ??... thanks!!

---

### Post by Maheriano on 2011-05-15
Same problem here. Is there a fix?

---

### Post by markackerman8@gmail.com on 2011-05-20
same problem here ... arghhhhh

---

### Post by worik on 2011-06-20
As the error says you are using an obsolete driver

Get the latest: git clone git://linuxtv.org/media_build.git

Change directory into media_build

I had install libproc-processtable-perl package

Run ./build.sh.  It (and I do not like this) goes and gets the sources and tries to build them.

This worked for me.  Now if only my device was supported....

Worik

---

### Post by calande on 2011-06-21
It won't work: 

```
$ ./build.sh
Checking if the needed tools are present
./check_needs.pl
cat: /etc/system-release: No such file or directory
cat: /etc/redhat-release: No such file or directory
ERROR: please install "lsdiff", otherwise, build won't work.
I don't know distro . So, I can't provide you a hint with the package names.
Be welcome to contribute with a patch for media-build, by submitting a distro-specific hint
to linux-media@vger.kernel.org
Build can't procceed as 1 dependency is missing at ./check_needs.pl line 98.
*** ERROR. Aborting ***
```

---

### Post by Canarygsr on 2011-06-22
Hi

sudo apt-get install patchutils

will install lsdiff and I also had to install libproc-processtable-perl

---

### Post by calande on 2011-06-22
Now they built properly, and I was able to make install them properly. However, I still can scan only HD TV channels :(

---

