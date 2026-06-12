---
title: "Do I need Header Files"
date: 2012-03-26
forum: General Help
---

### Post by Binary-Synapse on 2012-03-26
Hello.
 
I need header files to allow new programs to be compiled in my system, right??
 
But imagine i have kernel 2.6.32-22
 
Do I need linux-headers-2.6.32-22 AND linux-headers-2.6.32-22**-generic** also?
 
Whats the difference between the two packages?
 
Thank you

---

### Post by WorMzy on 2012-03-26
> **Binary-Synapse said:**
> Hello.
 
I need header files to allow new programs to be compiled in my system, right??
No. You only need kernel header files to compile kernel modules.

> Do I need linux-headers-2.6.32-22 AND linux-headers-2.6.32-22-generic also?

Whats the difference between the two packages?

Can't help you there. Ubuntu's packaging system doesn't make sense at the best of times. There's a size difference between the two packages that suggests that linux-headers-2.6.32-22 is the more complete package.

[http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22](http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22)
[http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22-generic](http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22-generic)

---

### Post by Binary-Synapse on 2012-03-26
> **WorMzy said:**
> No. You only need kernel header files to compile kernel modules.
 
But don't I need linux-header files to compile some programs?
I ask this because I have my Realtek WLAN driver that fails its compile process, unless I have my header-files installed.
 
 
> **WorMzy said:**
> Can't help you there. Ubuntu's packaging system doesn't make sense at the best of times. There's a size difference between the two packages that suggests that linux-headers-2.6.32-22 is the more complete package.
 
[http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22](http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22)
[http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22-generic](http://packages.ubuntu.com/lucid/linux-headers-2.6.32-22-generic)
 
So... are you saying... should I install both??
 
Thank you

---

### Post by jerome1232 on 2012-03-26
linux-headers-xxxxxxxx-generic depends on linux-headers-xxxxxxxxxxx, but the opposite is not true.


if install the -generic one, the other one will be installed as well.

---

### Post by Yellow Pasque on 2012-03-26
> **Binary-Synapse said:**
> But don't I need linux-header files to compile some programs? I ask this because I have my Realtek WLAN driver that fails its compile process, unless I have my header-files installed.
The "driver" is called a kernel module in Linux, and, as pointed out, you need kernel headers to build kernel modules.

---

### Post by Binary-Synapse on 2012-03-27
OK.
 
As mentioned, there is a big size difference between the two, but just to play it safe, I applied both (generic and non-generic headers).
 
Thank you.

---

