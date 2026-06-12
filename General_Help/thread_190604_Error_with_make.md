---
title: "Error with make"
date: 2006-06-06
forum: General Help
---

### Post by yumigator on 2006-06-06
I'm using make to compile a few drivers, and I'm getting errors. I cd to the directory and then type sudo make, and I get the following error:
```
Makefile:8: /lib/modules/2.6.15-23-386/build/.config: No such file or directory
make: *** No rule to make target `/lib/modules/2.6.15-23-386/build/.config'.  Stop.
```
I know that /lib/modules/2.6.15-23-386/build must be a symbolic link to another directory since it doesn't exist on my machine right now. Where am I supposed to link the file to to get my make to work?

Thanks in advance for any help.

---

### Post by xtacocorex on 2006-06-06
You need to install the kernel source package:
sudo apt-get install linux-headers

---

### Post by yumigator on 2006-06-06
Thanks, make works now. I don't know why apt doesn't see that as required when you install build-essential. It worked with Breezy.

Anyway, I'm still seeing some issues I'm hoping someone can help me with. I'm trying to compile the MA521 driver from [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/). When I go to the directory and run make, I get the following output:
```
yumigator@Dell-8100-Linux:~$ cd ~/Desktop
yumigator@Dell-8100-Linux:~/Desktop$ dir
initconf-0.1.tar.gz   initng-ifiles-0.0.5.tar.bz2  rtl8180-0.21
initng-0.6.7.tar.bz2  ndis
yumigator@Dell-8100-Linux:~/Desktop$ cd rtl8180-0.21
yumigator@Dell-8100-Linux:~/Desktop/rtl8180-0.21$ sudo make
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/yumigator/Desktop/rtl8180-0.21 MODVERDIR=/home/yumigator/Desktop/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/yumigator/Desktop/rtl8180-0.21/ieee80211_rx.o
  CC [M]  /home/yumigator/Desktop/rtl8180-0.21/ieee80211_tx.o
  CC [M]  /home/yumigator/Desktop/rtl8180-0.21/ieee80211_wx.o
  CC [M]  /home/yumigator/Desktop/rtl8180-0.21/ieee80211_module.o
  CC [M]  /home/yumigator/Desktop/rtl8180-0.21/ieee80211_crypt.o
  CC [M]  /home/yumigator/Desktop/rtl8180-0.21/ieee80211_crypt_wep.o
/home/yumigator/Desktop/rtl8180-0.21/ieee80211_crypt_wep.c:27:2: warning: #warning CONFIG_CRYPTO_ARC4 is required to build this module.
  CC [M]  /home/yumigator/Desktop/rtl8180-0.21/r8180_core.o
/home/yumigator/Desktop/rtl8180-0.21/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/yumigator/Desktop/rtl8180-0.21/r8180_core.c:3632: error: ‘struct pci_dev’ has no member named ‘slot_name’
make[2]: *** [/home/yumigator/Desktop/rtl8180-0.21/r8180_core.o] Error 1
make[1]: *** [_module_/home/yumigator/Desktop/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make: *** [2.6] Error 2
```
I'm pretty new to this, and I can't even understand this at all. What do I need to get this to compile correctly?

Thanks

---

### Post by xtacocorex on 2006-06-06
Most people don't need the kernel source (linux-header), so it isn't included by default or with build-essential.

FYI, You don't need to run make as root, just make install as root. If you want to build a .deb package for it, run checkinstall instead of the make install as root. To do this, you need to do: sudo apt-get install checkinstall. If you are going to do a decent bit of compiling, I'd suggest also installing xlib-dev.

I think this might be the second problem. From the website it says:
> 2) In order to use encryption with those drivers You willneed crypto API support in your kernel with ARC4 enabled and CRC32 functions in your kernel. 
I don't know if the default kernels support this.

The website also said that you need to use the CVS source for kernels greater than 2.6.12, didn't know if that's what you downloaded or not.

---

