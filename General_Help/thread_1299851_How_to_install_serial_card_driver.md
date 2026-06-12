---
title: "How to install serial card driver"
date: 2009-10-24
forum: General Help
---

### Post by MickSulley on 2009-10-24
Hi,

I just bought a serial card for my desktop, they have supplied a driver which works if I go through the instructions in their readme file, but after a re-boot the driver is not active and I have to run -
insmod mcs9865.ko

and
insmod mcs9865-isa.ko
again.

What is the correct way to install the driver properly?

Thanks

Mick

---

### Post by lswb on 2009-10-24
Add the module names on separate lines to the file /etc/modules. (The file must be edited as root)

---

### Post by MickSulley on 2009-10-24
I just tried that and it didn't work.  My modules file now has - 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
sbp2
# these next 2 added 24 Oct 09
mcs9865.ko
mcs9865-isa.ko

Do I need to put the mcs files in a particular directory?  At the moment I just put all the driver files into a temp directory and ran make there.

Thanks

Mick

---

### Post by lswb on 2009-10-24
Mormally modules are in a /lib/modules/<kernel-version> directory tree somewhere, where <kernel-version> is the string returned by the command "uname -r"

I'm not sure if using the complete path to a module will work in /etc/modules, but that is the first thing I would try. If that doesn't work, you could try placing a copy of the modules in one of the subdirectories of the /lib/modules/$(uname -r) , perhaps /lib/modules/$(uname -r)/kernel/drivers/serial/

Please post again with your results.

Just FYI if you didn't know, but if you install a kernel upgrade it will be necessary to recompile the modules for the new kernel.

---

### Post by MickSulley on 2009-10-24
Still not working.  There were already files with those names in /lib/modules/$(uname -r)/kernel/drivers/serial/ so I renamed them as .old and put mine in there as well.  I have since done a diff on them and the originals were my files, so I guess the original install put them there.

I could use a script to run insmod at startup, but this does not sound like the correct way to do this sort of thing.  What do you think?

Cheers

Mick

---

### Post by lswb on 2009-10-24
Try using just the module name without the ".ko" at the end. Seems silly but that is probably why it's not working.

---

### Post by MickSulley on 2009-10-24
Yes that's it!  Now it works fine.

Thanks for your help!

Mick

---

### Post by afro22 on 2009-11-23
Can you send me mcs9865.ko file to afro (at) grape (dot) sk?

I have problem with compiling from sources. I don't have compiled file.
Many thanks

---

