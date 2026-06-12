---
title: "Win4Lin Help?"
date: 2005-02-11
forum: General Help
---

### Post by mhancoc7 on 2005-02-11
I have finally got my compaq armada 1750 laptop dual booting Ubuntu and WinXP. Now I want to try and get Win4Lin setup to run Windows 98se. I have all the necessary tools, but I am a linux newbie and am a bit confused about how to go about getting this setup. I have read most of the posts regarding Win4Lin, but I am having trouble following them. Is there a How To for Win4Lin on Ubuntu or can some one walk me through the setup.

Thanks and God Bless, Jereme

---

### Post by NaughtyusMaximus on 2005-02-11
[QUOTE=mhancoc7]I have finally got my compaq armada 1750 laptop dual booting Ubuntu and WinXP. Now I want to try and get Win4Lin setup to run Windows 98se. I have all the necessary tools, but I am a linux newbie and am a bit confused about how to go about getting this setup. I have read most of the posts regarding Win4Lin, but I am having trouble following them. Is there a How To for Win4Lin on Ubuntu or can some one walk me through the setup.

Thanks and God Bless, Jereme[/QUOTE]


I'll do my best..
What you need to do first is go to kernel.org, and download the tar.bz2 for the latest supported kernel sources (2.6.10)

Then go to [www.netraverse.com](www.netraverse.com) and download the latest kernel patches (mki-adapter - whatever the latest is, and Kernel2.6.10-...-.patch)

untar the kernel sources to /usr/src/linux-2.6.10 then:


cd /usr/src/linux-2.6.10
sudo cat /dir/of/patches/mki-adapter_latestversion.patch | sudo patch -p1
sudo cat /dir/of/patches/Kernel-patch-latestversion.patch | sudo patch -p1

sudo make menuconfig
 --select the Netraverse Win4Lin patches, and save your kernel config
sudo make-kpkg clean
sudo make-kpkg --revision=win4lin1.0 --initrd kernel_image
cd ..
sudo dpkg -i *.deb
sudo reboot

select your new kernel on reboot (2.6.10), download the latest install program from [www.netraverse.com](www.netraverse.com), and from here you can follow their instructions for install.  In order to load your windows cd, you *may* need to open a terminal and type:

sudo loadwindowsCD

---

