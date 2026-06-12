---
title: "my kernel headers dont match current kernel"
date: 2006-06-12
forum: General Help
---

### Post by airzer0 on 2006-06-12
i updated to dapper from breezy with sudo apt-get update, then sudo apt-get upgrade. dapper will not load into breezy but now it says kernel headers don't match. so i think i need to remove my headers and reinstall them but im not sure  how to do that. thnks in advance

---

### Post by az on 2006-06-12
1.  try

sudo apt-get dist-upgrade

2.  If you get any errors, try

sudo apt-get -f install

3.  Why do you need the linux-headers?  Install the linux-headers-386 package (or 686, k7, smp, whatever) and that will also install the latest version of the linux-headers for your kernel.

But seriously, why do you need them?  A lot of hardware now just works fine - no need to recompile.

---

### Post by airzer0 on 2006-06-12
ok i have done all of that but when i try to install my nvidia driver it says warning kernel headers do not match current kernel. i try to load into daper and it hangs on mounting root drive. i know reinstalling ubuntu is a quick and easy fix but i want to learn how to fix it. so any help would be appriciated. right now using brezzy but at uname -r it says 2.6.16 so how do i change that back to the breezy?

---

### Post by az on 2006-06-12
[QUOTE=airzer0]ok i have done all of that but when i try to install my nvidia driver it says warning kernel headers do not match current kernel. i try to load into daper and it hangs on mounting root drive. i know reinstalling ubuntu is a quick and easy fix but i want to learn how to fix it. so any help would be appriciated. right now using brezzy but at uname -r it says 2.6.16 so how do i change that back to the breezy?[/QUOTE]
If you can't boot into the root filesystem with the Dapper kernel, you have not dist-upgraded to dapper.  You have to fix that before you worry about your video card.

You need to have all your repos pointing to Dapper.  Then apt-get update and apt-get dist-upgrade.

You installed the video drivers by hand?  What's wrong with the ones in the Dapper repo?  Just go with that.

---

### Post by airzer0 on 2006-06-13
ok thanks for your help i have gedit /etc/apt/soruces.list i changed all brezzy to dapper saved and then sudo apt-get update then sudo apt-get dist-upgrade 3 or 4 times every time it finishes. then i restart and pick 2.6.15 dapper and it hangs on mounting root drive. so what your saying is that it is not complete? would it be better to upgrade from a disk ? oh and i have done all of this from my breezy terminal. i will certanily try again though. could it be something else?

---

### Post by airzer0 on 2006-06-13
ok everthing is all good until this, there are a few errors, how should i procced?
Unpacking replacement libgstreamer-gconf0.8-0 ...
Preparing to replace gstreamer0.8-misc 0.8.12-0unofficialubuntu1 (using .../gstreamer0.8-misc_0.8.12-1ubuntu2_i386.deb) ...
Unpacking replacement gstreamer0.8-misc ...
dpkg: error processing /var/cache/apt/archives/gstreamer0.8-misc_0.8.12-1ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/gstreamer-0.8/libgstgoom.so', which is also in package gstreamer0.8-visuals
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: regarding .../libwavpack0_4.32-2ubuntu2_i386.deb containing libwavpack0:
 libwavpack0 conflicts with gstreamer0.8-misc (<< 0.8.12-1ubuntu2)
  gstreamer0.8-misc (version 0.8.12-0unofficialubuntu1) is installed.
dpkg: error processing /var/cache/apt/archives/libwavpack0_4.32-2ubuntu2_i386.deb (--unpack):
 conflicting packages - not installing libwavpack0
Preparing to replace gthumb 3:2.7.1-0ubuntu1~breezy1 (using .../gthumb_3%3a2.7.6-0ubuntu1_i386.deb) ...
Unpacking replacement gthumb ...
Selecting previously deselected package gtk2-engines-ubuntulooks.
Unpacking gtk2-engines-ubuntulooks (from .../gtk2-engines-ubuntulooks_0.9.11-1_i386.deb) ...
Replacing files in old package ubuntu-artwork ...
Preparing to replace guile-1.6-libs 1.6.7-1ubuntu3 (using .../guile-1.6-libs_1.6.7-2_i386.deb) ...
Unpacking replacement guile-1.6-libs ...
Preparing to replace python2.4-gnome2 2.12.1-0ubuntu1 (using .../python2.4-gnome2_2.12.4-0ubuntu1_i386.deb) ...
Unpacking replacement python2.4-gnome2 ...
Preparing to replace hal-device-manager 0.5.3-0ubuntu14 (using .../hal-device-manager_0.5.7-1ubuntu18_all.deb) ...
Unpacking replacement hal-device-manager ...
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer0.8-misc_0.8.12-1ubuntu2_i386.deb
 /var/cache/apt/archives/libwavpack0_4.32-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by airzer0 on 2006-06-13
OWNED! all i wanted was a strait answer....big props to azz

---

### Post by airzer0 on 2006-06-13
ok i am in dapper but when i went to remove automatix and my nvidia driver i got this:
Removing automatix ...
Setting up cpad-kernel-source (0.9-10) ...
Warning: kernel headers don't match running Linux version.
Building cpad module for Linux 2.6.16 (this may take a few minutes)...dpkg: error processing cpad-kernel-source (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 cpad-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

that is why i was asking about my kernel headers,

---

