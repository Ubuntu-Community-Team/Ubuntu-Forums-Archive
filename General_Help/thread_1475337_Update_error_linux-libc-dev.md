---
title: "Update error: linux-libc-dev"
date: 2010-05-06
forum: General Help
---

### Post by Oddbio on 2010-05-06
Hello, I have done a completely fresh install of Ubuntu 10.04.
As soon as I installed it and checked for updates there were a few, but I got an error for the package linux-libc-dev.

I should make it known that since I got this error about 2 days ago, there have been several more updates issued for other packages, but I still get the same error for this package.

Everything else installs fine and currently linux-libc-dev is the only package in my list.

When I try to install it via the update manager I get a popup window with the following error message:

> E: /var/cache/apt/archives/linux-libc-dev_2.6.32-22.33_i386.deb: unable to stat `./usr/include/asm-generic/mman.h' (which I was about to install)


To get more information I also ran it from the terminal:
sudo apt-get update
sudo apt-get upgrade

> (Reading database ... 147293 files and directories currently installed.)
Preparing to replace linux-libc-dev 2.6.32-21.32 (using .../linux-libc-dev_2.6.32-22.33_i386.deb) ...
Unpacking replacement linux-libc-dev ...
dpkg: error processing /var/cache/apt/archives/linux-libc-dev_2.6.32-22.33_i386.deb (--unpack):
 unable to stat `./usr/include/asm-generic/mman.h' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-libc-dev_2.6.32-22.33_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I am using Genome and my current kernel is:
2.6.32-22-generic


When I click on "description of update" in the update manager for this package it gives the following information under the "changes" tab:

> Changes for the versions:
2.6.32-21.32
2.6.32-22.33

Version 2.6.32-22.33: 

  [ Andy Whitcroft ]

  * SAUCE: ACPI: EC: Allow multibyte access to EC (v3)
    - LP: #526354

  [ Tim Gardner ]

  * ubuntu: rtl8192se -- update to version 0015.0127.2010
    - LP: #567016

Under the "description" tab I see:

> This package provides headers from the Linux kernel.
These headers are used by the installed headers for GNU glibc and other system libraries. They are NOT meant to be used to build third-party modules for your kernel. Use linux-headers-* packages for that.




Thank you for any help that can be provided.

and please feel free to ask for additional information.

---

### Post by Oddbio on 2010-05-07
My laptop model is:
SONY VAIO PCG-K45

its GPU is an:
ATI Radeon IGP 345m

---

### Post by 4String_Gal on 2010-05-31
I am having a similar problem. When I tried to do the updates from the Update Manager, I got an error. Then I tried using apt, here's the error I got:

The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7) but 2.11.1-0ubuntu7.1 is to be installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.1) but 2.11.1-0ubuntu7 is to be installed
  libc6-i386: Depends: libc6 (= 2.11.1-0ubuntu7.1) but 2.11.1-0ubuntu7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

apt-get -f install didn't help:

$sudo apt-get -f install

(Reading database ... 198740 files and directories currently installed.)
Preparing to replace libc6 2.11.1-0ubuntu7 (using .../libc6_2.11.1-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.1_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/gconv/GB18030.so')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.11.1-0ubuntu7.1); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.11.1-0ubuntu7.1); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 libc6-i386

Also, mysteriously, my nvidia driver is not working correctly anymore, (the screen is shifted over to the left, which happened before I installed the real nvidia driver when I had 9.10), and I got a warning message about graphics on a reboot after I tried to do my updates. And now neither Totem or Gnome MPlayer will play any of my .wav files. I think it's all related. I can start JACK.

Help!

---

