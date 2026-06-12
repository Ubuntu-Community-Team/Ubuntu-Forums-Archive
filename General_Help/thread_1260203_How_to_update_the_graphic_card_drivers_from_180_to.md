---
title: "How to update the graphic card drivers from 180 to 185"
date: 2009-09-07
forum: General Help
---

### Post by hihihi100 on 2009-09-07
[SIZE=1]Hi there:

It seems some of the problems I have with the graphics might have to do with the outdated graphic card drivers I use, currently, 180. 

The one I use: NVIDIA UNIX x86 Kernel Module  180.44

The one I need: Im not really sure, but I believe it is FreeBSD &#8211; x86, version 185.18.36 (I say Im not sure, because in [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) there are another X86 compatible drivers (Solaris x64/x86). Which one should I download?

Secondly, I have downloaded the first one (FreeBSD), and I have been looking for an icon or something to update the drivers, but found nothing, how did u update your graphic card drivers? Not in Hardware drivers, neither in restricted drivers manager. However, in the downloaded archives I found a file:

Installation of the NVIDIA Accelerated Graphics Driver"
    @echo "185.18.36 for FreeBSD is now complete.  You can now"
    @echo "run the nvidia-xconfig utility to automatically update"
    @echo "your X server configuration file.  Please see the README"
    @echo "for details if you wish to update your X configuration"
    @echo "file manually."

How do I run the xconfig utility?

Or, if I cannot do it, how do i manually install it?

Cheers

Please, give me a detailed answer, Im a dummie[/SIZE]

---

### Post by NoaHall on 2009-09-07
What OS are you trying to install on? If you're using Ubuntu, you do not need the BSD one, you need the Linux one. To install, you need to remove EVERY nvidia graphics driver before hand. Do not attempt to install if you haven't removed it. To update it, use "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by Strongman332 on 2009-09-07
try this source and your os should update them by its self

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by hihihi100 on 2009-09-08
No graphics card drivers in the laptop, not even in Hardware Drivers, now I dont see recommendations, but when I open a terminal and paste the code, this is what I get:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090908164309

Am I doing something wrong?

cheers

---

### Post by hihihi100 on 2009-09-08
ignore this one

---

