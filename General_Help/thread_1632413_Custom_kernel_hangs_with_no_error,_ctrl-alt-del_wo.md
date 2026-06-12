---
title: "Custom kernel hangs with no error, ctrl-alt-del works"
date: 2010-11-27
forum: General Help
---

### Post by Darxus on 2010-11-27
It hangs *after* mounting my root partition, and switching to framebuffer.  And ctrl-alt-del causes a normal shutdown - everything gets told to exit.

This where it hangs:
[http://www.chaosreigns.com/kernel/IMG_9643.jpg.html](http://www.chaosreigns.com/kernel/IMG_9643.jpg.html)

This is my config:
[http://www.chaosreigns.com/kernel/config-2010-11-27-02](http://www.chaosreigns.com/kernel/config-2010-11-27-02)

lspci output:
[http://www.chaosreigns.com/kernel/lspci.txt](http://www.chaosreigns.com/kernel/lspci.txt)

Based on the mainline defaults.  I made sure ext4 is compiled in, SCSI, SATA and PATA support...   sda1 is my root partition.  sdb1 is a data drive.  The drives are SATA.

I need to rebuild from source to test some stuff for wayland.

---

### Post by Darxus on 2010-11-27
I built without an initrd because that situation looks like a mess under ubuntu:  

"Note: I couldn't get the above scripts to help in generating an initrd for the kernel...."
"Note (Michael): that is because you need to include the right package scripts to build the initrd..."
- [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I tried to get that to work and couldn't.

And I need a kernel source tree more recent than is available in ubuntu packages.  

I just wish I could get a decent error message.

---

### Post by Darxus on 2010-11-27
lsmod output after booting a working kernel from a regular ubuntu package in rescue mode and dropping to a (non-network) root shell:  
[http://www.chaosreigns.com/kernel/lsmod.txt](http://www.chaosreigns.com/kernel/lsmod.txt)

---

### Post by Darxus on 2010-11-27
I tried deleting everything from /etc/init except mountall.conf.  When I booted to the working ubuntu kernel, it remounted my root partition read-write.  When I booted my custom kernel it didn't.  

So while it does apparently manage to mount my root partition once during boot, it looks like the problem is in that area.

---

### Post by Darxus on 2010-11-27
Tried adding CONFIG_PATA_AMD, same result.
[http://www.chaosreigns.com/kernel/config.2010-11-27-03](http://www.chaosreigns.com/kernel/config.2010-11-27-03)

---

### Post by Darxus on 2010-11-28
I tried an initrd again and it worked.

Steps I took to rebuild a kernel from source for a 2.6.37-rc3+ kernel:

git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
cd linux-2.6
cp /boot/config-`uname -r` .config # use .config of currently running kernel
yes "" | make oldconfig # use defaults of newer features
make clean && make && make modules && sudo make modules_install && sudo make install
mkinitramfs -o initrd.img `make kernelversion`
sudo mv initrd.img /boot/initrd.img-`make kernelversion`
sudo update-grub

Reboot.


I actually used the nouveau kernel tree ( git clone --depth 1 git://anongit.freedesktop.org/nouveau/linux-2.6 ), but I put Linus's in the steps above because it's probably useful for more people.

There's something weird going on with the nouveau tree that requires replacing:

`make kernelversion` 

with:

`make kernelversion`+

It needs to match the directory created in /lib/modules by "make modules_install".  But I think the above should work with mainline.  And you should get the idea.

---

