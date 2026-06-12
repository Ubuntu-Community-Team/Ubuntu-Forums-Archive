---
title: "Eciadsl Problem"
date: 2010-12-16
forum: General Help
---

### Post by Nipuna on 2010-12-16
I asked this before but didn't get an answer. I am using ubuntu for 3 years now. But i am not very good with ubuntu.

Please Help Me even at this time. 

I don't have Internet for Ubuntu 10.10 But i used it with Ubuntu 9.04 via Eciadsl.
Now it isn't working because of this I won't be able to use ubuntu much. I am always using Internet so i need Internet on ubuntu It is the Major problem to stop using ubuntu :(

My Modem is Prolink H9601c so I have to use Eciadsl because it doesn't  have Drivers for Ubuntu. It has Linux drivers but doesn't work with  ubuntu.

When i try eciadsl-start as Root, I get this

```
root@nipuna-OEM:~# eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is missing... trying to mount
Preliminary USB device filesystem: failed to load
/usr/bin/eciadsl-start: line 263: fatal: command not found
cat: /proc/bus/usb/devices: No such file or directory
Loading UHCI support... Warning: uhci-hcd module doesn't exist
Warning: tun/tap module does not exist

[EciAdsl 2/5] Uploading firmware...

grep: /proc/bus/usb/devices: No such file or directory
grep: /proc/bus/usb/devices: No such file or directory
ERROR: modem not found
root@nipuna-OEM:~# 
```I think I have to install or Compile the Kernel to Support these UHCI and tun/tap module

So i installed uml-utilities

but It didn't work. Above error comes again. :(

Please Help. I am not Very Good with Ubuntu Like You Guys.

---

### Post by Nipuna on 2010-12-16
Why Nobody is Helping Me :(

I installed this and it is working with this package 

[http://packages.ubuntu.com/hu/lucid/base/linux-image-2.6.31-10-rt](http://packages.ubuntu.com/hu/lucid/base/linux-image-2.6.31-10-rt)

But I want to use it with the latest kernel 

Please Help.

---

