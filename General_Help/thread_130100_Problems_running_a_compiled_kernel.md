---
title: "Problems running a compiled kernel"
date: 2006-02-15
forum: General Help
---

### Post by Johnnetto on 2006-02-15
[FONT="Arial"][SIZE="4"][COLOR="Red"][/COLOR][/SIZE][/FONT][CENTER][/CENTER]
Hi. I was trying to compile a kernel so i could get support for my ADSL USB Conexant modem.

1) I went to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and got:

-linux-source-2.6.12_2.6.12-10.26_all.deb
-kernel-package_9.001ubuntu13_all.deb
-libc6_2.3.5-1ubuntu12_i386.deb
-libncurses5-dev_5.4-9ubuntu4_i386.deb
-build-essential_11.1_i386.deb
-cpp-3.4_3.4.4-6ubuntu8_i386.deb
-gcc-3.4_3.4.4-6ubuntu8_i386.deb
-gcc-3.4-base_3.4.4-6ubuntu8_i386.deb

-usbatm-20050217.tar (from [http://sourceforge.net/projects/accessrunner](http://sourceforge.net/projects/accessrunner))

2) Then I compiled the kernel:

-sudo dpkg build-essential_11.1_i386.deb
-moved linux-source-2.6.12_2.6.12-10.26_all.deb to /usr/src
-sudo dpkg -i linux-source-2.6.12_2.6.12-10.26_all.deb
-sudo tar jxvf linux-source-2.6.12_2.6.12-10.26_all.tar.bz2
-sudo dpkg -i kernel-package_9.001ubuntu13_all.deb
-decompressed usbatm-20050217.tar and pasted the files in     /usr/src/linux-source-2.6.12/drivers/usb/atm
-sudo -ln -s linux-source-2.6.12 linux
-sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
-sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb
-sudo dpkg -i gcc-3.4_3.4.4-6ubuntu8_i386.deb
-sudo dpkg -i libncurses5-dev_5.4-9ubuntu4_i386.deb
-sudo make menuconfig
Devices drivers->USB Suport-> USB DSL modem suport-> [M] Conexant AccesRunner USB Suport
-CC=gcc-3.4
-sudo make-kpkg --append-to-version=.conexant --initrd kernel-image

The compilation ended and then, when i tried to install the kernel with
-sudo dpkg -i kernel-image-2.6.12.conexant_10.00.Custom_i386.deb
it gave a dependency problem: i had initramfs-tools_0.32_all.deb and the package needed a version >0.36. So i went to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and there was no initramfs-tools > 0.36 for Breezy. I looked in the Dapper packages and found initramfs-tools_0.40. I installed it and all the packages it depended on (they were Dapper packages). Then I tried to install the new kernel and it went fine. When i reloaded i could choose the new and the old kernel with Grub. But then, an error ocurred (it´ll be too complicated to tell you about it, let´s just say i couldn´t get around it), so i erased my Ubuntu partition and reinstalled it. 
Everything goes fine now. I tried to compile the kernel again. When i get to install it, it gives me that dependency error again. I won´t install initramfs-tools_0.40 again.

I need your help. If i don´t get to install a custom kernel with USB ADSL Conexant support, i can´t access internet. I´m a newbie, and i don´t know what to do. 
I chose Ubuntu because the community is great. Maybe someone can help me. If you have a clue about why it asks me for an initramfs-tools >0.36, or what can i do to install a custom kernel without installing initramfs-tools 0.40 i will appreciate it.

---

### Post by Johnnetto on 2006-02-22
I solved the problem. I downloaded and installed kernel-package_9.001ubuntu5_all.deb instead of kernel-package_9.001ubuntu13_all.deb and then installed the kernel.

---

### Post by nrwilk on 2006-02-22
just to let you know.  There are MUCH easier ways to get and install packages in ubuntu.

If you want to install stuff, just open up synaptic and it will download and install everything for you.

Also, you may like the command line better.  In that case, the command would be:
```
sudo apt-get update
sudo apt-get install <package name>
```

Of course, you need to know what each package is called to do it the second way.

If you want to enable some extra (unsupported) repositories which have a WHOLE LOT more software, head down to the "ubuntu repository support" forum and check out the sticky which tells you how to do that.

---

### Post by Johnnetto on 2006-02-22
Well, I know that. But I can´t connect to the Internet using Ubuntu. That´s why I compiled the kernel with Conexant support. Now i´m trying to configure ppoe.
You were trying to help, so thanks.

---

### Post by nrwilk on 2006-02-22
hehe, I read far too little into the problem.  I knew why you were trying to compile the kernel, but I failed to connect the dots in my head.  Sorry!

---

