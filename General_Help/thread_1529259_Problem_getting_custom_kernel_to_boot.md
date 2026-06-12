---
title: "Problem getting custom kernel to boot"
date: 2010-07-12
forum: General Help
---

### Post by Pestery on 2010-07-12
Hello everyone.
I'm more or less a newbie to Linux in general as I've only been using them on and off for a few months. I've been trying to compile an Ubuntu kernel so that I can using RTAI but so far it hasn't worked. I've managed to configure and compile the kernel but it won't boot. I can select it fine in grub, but after I do I get a black screen with a flashing cursor in the top left and that's it. I've left it for 10 minute or so with no change.

I'm been following the method listed at [https://woc.uc.pt/deec/getFile.do?tipo=2&id=5690](https://woc.uc.pt/deec/getFile.do?tipo=2&id=5690)
The only difference is that I'm using Ubuntu 9.10 (Karmic) which has a kernel of 2.6.31 and I'm trying to install a 2.6.31.8 kernel with the RTAI patch. I've also tried installing a 2.6.32.2 kernel but found the same result.

The two kernels I've tried are straight from [www.kernel.org]("http://www.kernel.org") and the Ubuntu system I've currently got running is a clean install. My cpu is an AMD Athlon 64 X2. I'm running the 32bit version of Ubuntu though because the RTAI patches that are available for 64bit are quite old, but the x86 patches are more recent and can be used with Ubuntu.

In the configuration of the kernel the only options I've changed from the original Ubuntu configuration are:
-Enable loadable module support > Module versioning support = no
-Processor type and features > Processor family = Opteron/Athlon64/Hammer/K8
-Power management options > Power Management support = no
-Power management options > CPU Frequency scaling > CPU Frequency scaling = no
-Processor type and features > Support sparse irq numbering = no
-Processor type and features > Enable -fstack-protector buffer overflow detection = no

I'm not really sure what other information to provide. Any help or suggestions would be very welcome.

Thanks

Matthew

---

### Post by oratnek on 2010-08-02
Well, I think I have exactly the same problem with Pestery...

I tried to compile a vanilla kernel (2.6.31.8 ) with a RTAI (magma) patch on Ubuntu 9.10 which has a kernel 2.6.31.14-generic (or 2.6.31.22-generic), but I failed to boot. I got a black screen with blinking "_".
I try to use some other vanilla kernels (2.6.28.9, 2.6.31, 2.6.31.1, 2.6.32.13) and corresponding patches, some different versions of RTAI (3.7.1, 3.8, 3.8.1, vulcano, magma) and Ubuntu (9.04, 9.10, 10.04)...all got the same failure.

When I removed "quiet splash" from /usr/default/grub, I got a message

```
Decompressing Linux... Parsing ELF... done.
Booting the kernel.
```

Any configuration within grub (such as "i915.modeset=0" or "vdriver=vesa") didn't take effect.
Though I removed /etc/kernel/postinst.d/nvidia-common, nothing changed.
Remaking initrd by "mkinitramfs" and "update-grub" also failed to make the situation better.

During configuration, I tried both

```
$ sudo cp /boot/config-`uname -r` .config
```

and

```
$ sudo wget http://hart.sourceforge.net/files/config-2.6.28-rtai_i386
$ sudo cp config-2.6.28-rtai_i386 .config
```

which is suggested in one of the RTAI install tutorial. But the result was the same.

I disabled some of features due to errors:

```
CONFIG_SPARSE_IRQ=n
CONFIG_CC_STACKPROTECTOR=n
```

Also I tried to patch with /opt/rtai/base/arch/i386/patches/* to corresponding older kernel such as 2.6.23.x, it caused another error maybe due to file read failure. I didn't dig this problem deeper. 

Confirmed that compiled vanilla kernel without RTAI patch worked well, I doubt the compatibility of custom kernel and my hardwares.

Hardwares below:

Intel Core 2 Duo E7500
MSI G41M-P34

Does anyone kindly know the solution for us? Thanks in advance!

p.s. My final goal is to execute RTXI.

---

### Post by Pestery on 2010-08-06
Hi oratnek, I've found a fix to the problem! (Or tripped over it while wading through emails and forum topics on the rtai website)
The problem seems to be Grub2. For some reason it can't load the rtai modified kernel, however Grub Legacy can. If you down-grade to the old Grub then the kernel should boot.

Downgrading is pretty easy, however I'm dual booting with WindowsXP and also CentOS-5 (another Linux distro), all on different partitions on the same hard drive, and I accidentally overwrote my master-boot-record so that only Ubuntu would boot, oops. I spent the next several hours learning about chainloading and fixing my boot settings. If your dual booting with another OS then I suggest you check where you want to install stage1 of grub (/dev/sda for the master-boot-record of the hard drive, /dev/sda1 for the boot sector on partition 1, sda2 for partition 2, etc). Make sure you backup you original boot folder as there might be useful info in there if things hit the fan.
```
sudo apt-get purge grub-pc
sudo rm -rf /boot/grub
sudo apt-get install grub-legacy # try grub-pc I think if grub-legacy not found
sudo grub-install /dev/sda   # check this location
sudo update-grub
```You might want to edit  /boot/grub/menu.lst to remove the options "quiet splash" so you can see whats going on after grub, or you may not. I did initially, but not any more.

I also had to turn off the config_sparse_irq and the config_cc_stackprojector options due to errors.

By the way, I'm now using the 2.6.31.8 kernel version and rtai-3.8. If you install nvidia drivers before installing the new rtai-modified kernel then you need to remove nvidia-common while you install it. The process I took was:
```
cd /usr/src/linux
sudo patch -p1 < /usr/src/rtai/base/arch/x86/patches/hal-linux-2.6.31.8-x86-2.4-09.patch
sudo cp /boot/config-`uname -r` .config
sudo make oldconfig   #Just press Enter to all the prompts
sudo make xconfig
#configure the kernel
sudo make-kpkg clean
sudo make-kpkg --initrd kernel_image kernel_headers
cd /usr/src
sudo apt-get purge nvidia-common #remove nvidia-common so install the kernel
sudo dpkg -i linux-headers-2.6.31.8-rtai-3.8-rev0_2.6.31.8-rtai-3.8-rev0-10.00.Custom_i386.deb
sudo dpkg -i linux-image-2.6.31.8-rtai-3.8-rev0_2.6.31.8-rtai-3.8-rev0-10.00.Custom_i386.deb
sudo apt-get install nvidia-common #reinstall nvidia-common
```I hope this helps. Good luck.

---

### Post by oratnek on 2010-08-07
Dear Pestery, thank you for reply! Well, it seems that we individually found out the solution! Yesterday I also succeeded to boot the patched kernel under GRUB 0.97. Though in my case, I had to carry out some cut-and-try kernel configurations, maybe due to my hardware environment (and also it seemed to solve the problem upon graphic drivers).
Anyway, I'm encouraged very much to know that so many guys try to utilize this application and some of them have the same problem with me! I with us both luck!

---

