---
title: "Low boot screen resolution after installing nVidia drivers. 10.04"
date: 2010-04-30
forum: General Help
---

### Post by marshall.robert on 2010-04-30
Hi,

When I first installed I was very impressed by the boot screen looking so nice and fitting to my laptops 1280x800 resolution, but since I installed the nVidia drivers it has gone to a ridiculously low res (I reckon 640x480) and 8 bit colour :(

Is there a way I can get back the nice boot screen? And if so, how?


Thanks in advance,
Rob

---

### Post by anton_es on 2010-04-30
i had the same problem. installing the nvidia driver made all kinds of problems for me. what solved the low-res loginscreen was starting the nvidia config manager and setting the options there -
i have a laptop connected per vga to an 16:10 screen. I always disable the laptop screen since it f**ks up everything if you happen to open/close it, the system goes into hibernate or does other unexpected things.

well, after setting nvidia config and rebooting the loginscreen worked, BUT now my external keyboard+mouse connected by USB do NOT get recognized during loginscreen-startup. I have to unplug and replug both usb-cables for ubuntu to discover them.

VERY, VERY annoying.
all in all the dual-screen setup, compix management and overall ease of use in that area of computing is still sub-par on ubuntu.
sad, but true.

---

### Post by NoFearDJB on 2010-04-30
I'm also having this problem :(

---

### Post by doas777 on 2010-04-30
as I understand it, there is no good fix. 
Plymouth requires a KMS capable driver to do pretty boot, but IIRC the only kms capable driver is nouveau, but nouveau is not 3d accellerated in hardware (software only so is slooooow). so as I understand it, you need to choose between pretty boot and compiz/3da games. 
hopefully there will be a kms driver for nvidia soon.

---

### Post by NoFearDJB on 2010-04-30
I fixed my problem with the instructions from here!
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by marshall.robert on 2010-05-01
I can confirm this worked.

It did hang on the first reboot. I don't know whether I needed to or I was just being impatient, but I did a cold shut down after a while.

On second boot it threw an error, I think, but I didn't catch it. Booted fine none the less, though.

---

### Post by parth115 on 2010-05-16
> **NoFearDJB said:**
> I fixed my problem with the instructions from here!
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Works perfectly.. thank you...

---

### Post by Jetro on 2011-04-10
[s](I know I'm bumping)

It doesn't work for me, as it can only support a resolution of 1280x1024, it seems, and nothing higher than that. I myself have a 1920 x 1200 resolution, so it looks ugly anyway.

And this is a bug that has been adressed many times on Launchpad, but [whoever makes Ubuntu] has decided it is not important and not done anything with it. See for instance [here](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013).

If it's somehow fixed by later releases, consider yourself lucky. :D[/s]

I went to the wrong link, will update later

---

