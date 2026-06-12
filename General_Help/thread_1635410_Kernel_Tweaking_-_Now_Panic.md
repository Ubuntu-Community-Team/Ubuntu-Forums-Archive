---
title: "Kernel Tweaking - Now Panic"
date: 2010-12-01
forum: General Help
---

### Post by redilyn on 2010-12-01
Hi,

I have been playing around with tweaking the ubuntu kernel.

I do not know what I am doing, but I am trying to understand by playing.

Anyways, my first attempt worked well, no obvious performance difference but a successful working kernel none the less.

So I tried to go farther, but now I get a kernel panic on boot. 

Some of the things I changed are:
Timer freq 100mhz
Processor type Atom
Enabled preemption
Removed all vendor specific modules relating to laptops (Dell, Acer, etc) except ASUS and eeepc modules which I choose to build into the kernel
Removed all drivers which did not relate to my system

And some other stuff I don't recall.

I have a working kernel so I don't feel like starting from scratch, I would rather learn what I did wrong.

The error message I get is:
Kernel panic - not syncing: IO-APIC + timer doesn't work

Can someone give me a suggestion where to look for the problem? I am compiling the ubuntu 2.6.35.7 kernel with ubuntu patches.

Thanks

---

