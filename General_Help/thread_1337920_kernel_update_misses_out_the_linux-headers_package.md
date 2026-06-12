---
title: "kernel update misses out the linux-headers packages"
date: 2009-11-25
forum: General Help
---

### Post by chaopoch on 2009-11-25
Yesterday, There was linux kernel 2.6.31-15 update, but when the computer rebooted, the screen started to blink and the booting process stopped, then I rebooted with the old kernel 2.6.31-14 and found that the updates did not include linux-headers-2.6.31-15 and linux-headers-2.6.31-15-generic, so I installed these two packages manually and re-installed linux-image-2.6.31-15-generic, linux-libc-dev, then the system reboot successfully with new kernel 2.6.31-15.

I just wonder,

1. Why does the update miss out the packages linux-headers-2.6.31-15 and linux-headers-2.6.31-15-generic?

2. Are these two packages necessary?

Thanks.

---

### Post by Saxcore on 2009-11-26
Ah. I was wondering what was going on when I logged in. I'm currently booted into 2.6.31.14; I'm not too good at this Linux thing, how do I go about fixing the 2.6.31-15 kernel?

Cheers, Sam.

---

### Post by chaopoch on 2009-11-26
$ sudo apt-get install linux-headers-2.6.31-15 linux-headers-2.6.31-15-generic linux-image-2.6.31-15-generic linux-libc-dev

then reboot.

---

### Post by Saxcore on 2009-11-30
Hi, thanks for your help. I logged on to 2.6.31.15 in recovery mode (not in recovery mode the kernel is completely useless at the moment, it struggles to accept text input) and ran the command you specified. However, after rebooting back into non-recovery mode, it doesn't seem to have fixed the problem. I'm not sure if my problem is related or not.

I was wondering; did you have a blinking screen that seems to ignore any form of input when it blinks?

---

### Post by coffeecat on 2009-11-30
To those not getting their linux headers updated with a kernel upgrade, go into Synaptic and make sure the linux-headers-generic package (no numbers in the name) is marked as installed. If not, install it. It's a metapackage that ensures you always get the latest version of the headers installed. It should have been installed in a default installation so if it is not there in your system, are you sure you didn't unmark it?

---

### Post by slakkie on 2009-11-30
> **coffeecat said:**
> To those not getting their linux headers updated with a kernel upgrade, go into Synaptic and make sure the linux-headers-generic package (no numbers in the name) is marked as installed. If not, install it. It's a metapackage that ensures you always get the latest version of the headers installed. It should have been installed in a default installation so if it is not there in your system, are you sure you didn't unmark it?

That package wasn't in older Ubuntu versions. It got introduced in Hardy: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-headers-generic](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-headers-generic)

---

