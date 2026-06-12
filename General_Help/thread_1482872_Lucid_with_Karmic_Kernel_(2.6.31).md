---
title: "Lucid with Karmic Kernel (2.6.31)"
date: 2010-05-14
forum: General Help
---

### Post by nereid on 2010-05-14
Hi folks,

my Eee PC has various troubles with the current Lucid kernel (2.6.32). These include, that the wifi won't work and that I can't use hibernate. A netbook without wifi is a little bit useless ;)

I even tried the usual bugfixes, that you can find in the web (installing the original RAlink drivers, updating to 2.6.33), but nothing really worked.

As a consequence, I downgraded to Karmic again, were everything just worked fine.

My question is now, is it possible to run Lucid with the older kernel available in Karmic?

Cheers and thanks in advance.

---

### Post by slushpuppisan on 2010-06-22
Yes, it's definitely possible. I use the 2.6.31 kernel in Lucid when I want to go on battery power because there's a bug in the newer ones that constantly wakes the CPU up. If you don't need to patch anything, you can get the mainline kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . You might also want to try the .35-rc1-lucid kernel and see if it fixes your problems. I'm a little shaky on what a "mainline" kernel is, in Synaptic the package description says they have Ubuntu patches, but I'm not sure if they really do. Either way, they both work (.31 and .35 that is). If you want to install 32-bit, download [linux-headers-2.6.31-02063113-generic_2.6.31-02063113_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31.13-karmic/linux-headers-2.6.31-02063113-generic_2.6.31-02063113_i386.deb")
[linux-headers-2.6.31-02063113_2.6.31-02063113_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31.13-karmic/linux-headers-2.6.31-02063113_2.6.31-02063113_all.deb")
[linux-image-2.6.31-02063113-generic_2.6.31-02063113_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31.13-karmic/linux-image-2.6.31-02063113-generic_2.6.31-02063113_i386.deb")

Double-click to install, and after you're done, you have to update grub to have them added to the boot menu:
sudo update-grub

I think that's the gist of it but check out section 3.0 in [http://ubuntuforums.org/showthread.php?t=1503491&highlight=toshiba+a505](http://ubuntuforums.org/showthread.php?t=1503491&highlight=toshiba+a505) if you want more detailed instructions.
[]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31.13-karmic/linux-image-2.6.31-02063113-generic_2.6.31-02063113_i386.deb")

---

