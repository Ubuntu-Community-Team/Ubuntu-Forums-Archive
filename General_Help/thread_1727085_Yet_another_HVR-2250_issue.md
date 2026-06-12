---
title: "Yet another HVR-2250 issue"
date: 2011-04-12
forum: General Help
---

### Post by The_K4 on 2011-04-12
I have been trying to get my 2250 working and have hit a wall.  I followed the standard instructions:

```
sudo apt-get install mercurial libncurses5-dev unzip
wget -c http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip wget -c http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget -c http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw 
wget -c http://www.steventoth.net/linux/hvr22xx/extract.sh
sh extract.sh
sudo cp *fw /lib/firmware 
hg clone http://kernellabs.com/hg/saa7164-stable/ 
cd saa7164-stable 
make CONFIG_DVB_FIREDTV:=n 
```

However when I try and compile with the make I get the following:
```
make -C /home/k4/Downloads/saa7164-stable/v4l 
make[1]: Entering directory `/home/k4/Downloads/saa7164-stable/v4l'
No version yet, using 2.6.35-28-generic
make[1]: Leaving directory `/home/k4/Downloads/saa7164-stable/v4l'
make[1]: Entering directory `/home/k4/Downloads/saa7164-stable/v4l'
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
make[1]: Leaving directory `/home/k4/Downloads/saa7164-stable/v4l'
make[1]: Entering directory `/home/k4/Downloads/saa7164-stable/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.35-28-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/k4/Downloads/saa7164-stable/v4l/firmware'
make[2]: Leaving directory `/home/k4/Downloads/saa7164-stable/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/k4/Downloads/saa7164-stable/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/k4/Downloads/saa7164-stable/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-28-generic/build
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/k4/Downloads/saa7164-stable/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.o
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c:252: error: implicit declaration of function 'kfree'
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c:314: error: implicit declaration of function 'kzalloc'
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c:314: warning: assignment makes pointer from integer without a cast
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c:365: warning: assignment makes pointer from integer without a cast
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.c:1314: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/k4/Downloads/saa7164-stable/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/k4/Downloads/saa7164-stable/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/k4/Downloads/saa7164-stable/v4l'
make: *** [all] Error 2

```

I am really at a loss as to what to do now.  Any help would be really appreciated.

---

