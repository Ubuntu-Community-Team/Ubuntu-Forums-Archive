---
title: "No rule to make target"
date: 2010-09-27
forum: General Help
---

### Post by FluidBlow on 2010-09-27
Hello everybody,

In order to use the driver rt8712, I need to compile it.
So in the directory of the driver's makefile, I did a "make" and few errors followed :
```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/2.6.32-5-amd64/build M=/home/baptiste/rtl8712/driver  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-5-amd64'
/home/baptiste/rtl8712/driver/Makefile:11: /usr/src/linux-headers-2.6.32-5-common/config: No such file or directory
make[4]: *** No rule to make target `/usr/src/linux-headers-2.6.32-5-common/config'.  Stop.
make[3]: *** [_module_/home/baptiste/rtl8712/driver] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-5-amd64'
make: *** [modules] Error 2
 
```How can I do to find the missing file ? (wich I think is a .config file in /usr/src/uname -r/ folder)

I'm under Debian squeeze 64 bits

Thanks for any help !

---

### Post by andrewthomas on 2010-09-27
```
sudo apt-get install build-essential checkinstall
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by FluidBlow on 2010-09-28
Ah, I forgetted about the config file in the source folder.

But when I execute it, i got errors like :
```

root@debian:/home/baptiste/rtl8712/driver# ./config
./config: line 6: CONFIG_RTL8711: command not found
./config: line 7: CONFIG_RTL8712: command not found
./config: line 10: CONFIG_USB_HCI: command not found
./config: line 11: CONFIG_SDIO_HCI: command not found
./config: line 14: CONFIG_MP_INCLUDED: command not found
./config: line 16: CONFIG_PLATFORM_I386_PC: command not found
./config: line 17: CONFIG_PLATFORM_ARM_S3C: command not found
./config: line 18: CONFIG_PLATFORM_ARM_PXA: command not found
./config: line 19: CONFIG_PLATFORM_MIPS_RMI: command not found
./config: line 20: CONFIG_PLATFORM_RTK_DMP: command not found
./config: line 21: CONFIG_PLATFORM_MIPS_PLM: command not found
./config: line 22: CONFIG_PLATFORM_RTD2880B: command not found
./config: line 23: CONFIG_PLATFORM_MSTAR389: command not found
./config: line 25: CONFIG_MLME_EXT: command not found
./config: line 26: CONFIG_DRVEXT_MODULE: command not found

```

Why ?

---

### Post by andrewthomas on 2010-09-28
post the output of 

```
aptitude search build-essential
```

---

### Post by FluidBlow on 2010-09-28
Well, I've just found how to solve my problem.

I downloaded the linux kernel source, and made a "make menuconfig" in it's directory, then I saved the config (with the defaults parameters) in the directory my driver wanted it to be (and renamed it "config").
And guess what ? It worked like a charm.

Thank you for your help.

---

### Post by FluidBlow on 2010-09-28
Well, I've just found how to solve my problem.

I downloaded the linux kernel source, and made a "make menuconfig" in it's directory, then I saved the config (with the defaults parameters) in the directory my driver wanted it to be (and renamed it "config").
And guess what ? It worked like a charm.

Thank you for your help.

---

### Post by musial on 2010-11-28
Hi, after some unsuccessful attempts to solve the very same problem for myself, I finally understood what the problem seems to be:

The RealTek driver's Makefile contains in line 6:
```
 export TOPDIR := $(PWD)
```which seems to confuse the Makefile infrastructure of the 2.6.32 kernels (at least) when the Makefile is re-included from the kbuild tree (then, $(PWD) is clearly somewhere else).

My quick solution was to replace the cited line in the Makefile with its actual target in clear text, e.g.

```
 export TOPDIR := /home/jimmy/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100601/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100601
```making both *make* and *make install *work perfectly.

I have to admit that I actually did this on debian squeeze, while the driver compilation worked out of the box on kubuntu 10.10 with 2.6.35 kernel. But as the problem was reported here, the answer belongs here, too. :)

---

