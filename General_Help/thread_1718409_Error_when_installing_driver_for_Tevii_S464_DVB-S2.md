---
title: "Error when installing driver for Tevii S464 DVB-S2 PCI"
date: 2011-03-31
forum: General Help
---

### Post by henz103 on 2011-03-31
I'm having problem installing the driver, getting error in "sudo make" step

Tevii S464 DVB-S2 PCI
Driver: [http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar](http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar)
OS: Ubuntu 10.10

Terminal log:

```
hany@hany-desktop:~/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000$ sudo make
make -C /home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l 
make[1]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
No version yet, using 2.6.35-28-generic
make[1]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
make[1]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.35

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

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
make[1]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.35-28-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
make[2]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-28-generic/build
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.o
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:252: error: implicit declaration of function 'kfree'
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:314: error: implicit declaration of function 'kzalloc'
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:314: warning: assignment makes pointer from integer without a cast
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:365: warning: assignment makes pointer from integer without a cast
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:1269: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
make: *** [all] Error 2
hany@hany-desktop:~/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000$
```


Any ideas?

Thanks

---

### Post by henz103 on 2011-04-01
bump

---

