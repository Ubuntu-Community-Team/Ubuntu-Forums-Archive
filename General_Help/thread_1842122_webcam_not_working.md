---
title: "webcam not working"
date: 2011-09-10
forum: General Help
---

### Post by sn0m on 2011-09-10
Hi guys
I got a new laptop today, asus K53E. Everything works a dream, is just the webcam which is upsidedown for some reason. 
koli@koli-K53E:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5120 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
koli@koli-K53E:~$ 

as you can see it is not listed and i suspect it is a proprietary webcam/driver. Does anybody know any good how to to turn in the right way.
Thanks
Sokol

---

### Post by snip3r8 on 2011-09-10
1:What version of ubuntu are you running?
2:if its a laptop the camera might not be usb,maybe try lspci.
3:There is also a highly rated piece of software for webcams in the software center called cheese webcam booth that you might want to try when all is working

---

### Post by sn0m on 2011-09-10
Hi Thanks for your answer.
I am running 11.04 64 bit.
I've tried lspci and this is the output:
koli@koli-K53E:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
koli@koli-K53E:~$ 
also
dmesg | grep video
[    1.412732] pci 0000:00:02.0: Boot video device
[    2.078570] ACPI Warning: _BQC returned an invalid level (20110112/video-473)
[   12.679999] Linux video capture interface: v2.00
[   12.685716] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5120)
[   12.693867] usbcore: registered new interface driver uvcvideo

sorry I'm not sure where to start
thanks
sokol

---

### Post by sn0m on 2011-09-10
sorry just found this but not sure how to get it going in ubuntu, any help is appreciated.
[https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=711492](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=711492)
Sokol

---

### Post by sn0m on 2011-09-15
Hi I got it working, 
Instructions as follow:
Hi,

Thanks for providing the requested information. I've just made
a new (test) release of v4l-utils (which includes libv4l) which
contains your laptop info in its upside down table, and as such
should fix (work around) the upside down issue for you.

You can download this new version here:
[http://people.fedoraproject.org/~jwrdegoede/v4l-utils-0.9.0-test.tar.bz2](http://people.fedoraproject.org/~jwrdegoede/v4l-utils-0.9.0-test.tar.bz2)

1. Install
==========

libv4l needs make, a working C-compiler (gcc), and libjpeg +
its header files to build. If you don't have these you need to install them
first. See your distributions documentation on how to install make and
the compiler (often called development tools / chain). For libjpeg,
you need to install the libjpeg62-dev under Debian/Ubuntu and the
libjpeg-devel package under Fedora / RHEL.

Howto install and test libv4l depends on your system. There are
different instructions for if you have a 32 bit system or a 64 bit system.
which is using multilib. A 64 bit system without multilib is the same as
a 32 bit system.

To find out what you have do:
ls -d /usr/lib64

If this command gives a "No such file or directory" error, use the
Non multilib instructions, if this command is successfull, you likely have multilib.

Note: I've received some reports that there us a /usr/lib64 directory on some 32
bit installs of Ubuntu. If you're quite sure you are running a normal (32 bit) version
of Ubuntu you likely are and you should follow the Non multilib instructions.

Ok, so you have a multilib system, to find out which (dubbed Fedora and Ubuntu
multilib, because those are the most well known examples, do):

ls -d /usr/lib32
If this command gives a "No such file or directory" error, use the Fedora multilib
instructions. If this command succeeds use the Ubuntu multilib instructions. Note
the ubuntu multilib instructions also apply to gentoo and the Fedora multilib instructions
also apply to [open]Suse.


Non multilib instructions:
--------------------------
tar xvfj v4l-utils-<version>.tar.bz2
cd v4l-utils-<version>/lib
make PREFIX=/usr
sudo make install PREFIX=/usr

Fedora Multilib instructions:
-----------------------------
Basic 64 bit install:
tar xvfj v4l-utils-<version>.tar.bz2
cd v4l-utils-<version>/lib
make PREFIX=/usr LIBDIR=/usr/lib64
sudo make install PREFIX=/usr LIBDIR=/usr/lib64

If you also want to use 32 bit apps (such as skype), you
will need to have the 32 bit libc headers installed, on Fedora
this can be done like this:
Fedora 10-: "sudo yum install glibc-devel.i386"
Fedora 11:  "sudo yum install glibc-devel.i586"
Fedora 12+: "sudo yum install glibc-devel.i686"
[open]Suse: install glibc-devel-32bit and gcc-32bit

Then do:
make clean
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32
sudo make install PREFIX=/usr

Ubuntu Multilib instructions:
-----------------------------
tar xvfj v4l-utils-<version>.tar.bz2
cd v4l-utils-<version>/lib
make PREFIX=/usr
sudo make install PREFIX=/usr

If you also want to use 32 bit apps (such as skype), you
will need to have the 32 bit libc headers installed, on Ubuntu
this can be done like this:
sudo apt-get install libc6-dev-i386
On gentoo this can be done like this:
sudo emerge -v app-emulation/emul-linux-x86-compat
Then do:
make clean
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32 LIBDIR=/usr/lib32
sudo make install PREFIX=/usr LIBDIR=/usr/lib32


2. Testing
==========
You have a chance that your webcam app use libv4l or have an appropriate
script starting it. In that case you don't have to do anything. Just run
the application. This is the most common situation with Ubuntu and Fedora
packages. If your problem remains unsolved, then your app might not use libv4l.
In that case start the application from a terminal like this:

Non multilib:
----------------
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so <your favorite webcam app>

Note on Ubuntu sometimes skype is using a wrapper script, so if skype
does not work try:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

Fedora multilib:
--------------------
For 64 bit applications (allmost all apps):
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so <your favorite webcam app>

For 32 bit applications (you only need it for proprietary softwares, which
don't have a 64 bit version, like skype):
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Ubuntu multilib:
--------------------
For 64 bit applications (allmost all apps):
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype

For 32 bit applications (you only need it for proprietary softwares, which
don't have a 64 bit version, like skype):
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Note on Ubuntu sometimes skype is using a wrapper script, so if skype
does not work try:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real


Please let me know if this version of v4l-utils turns the image the
right way up for you.

Thanks & Regards,

Hans

---

### Post by magicfab on 2011-09-20
Hi

I have the very same USB ID for my (upside down) webcam on Asus. This took care of it (while installing the latest libv4l-0):

sudo add-apt-repository ppa:libv4l/ppa
sudo apt-get update && sudo apt-get dist-upgrade -y

Worked for me on a Asus A53E laptop.

Good luck.

---

