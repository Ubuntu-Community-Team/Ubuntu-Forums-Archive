---
title: "ARM arch package confusion."
date: 2009-08-01
forum: General Help
---

### Post by mgillespie on 2009-08-01
I have a Marvell Sheevaplug on the way, and I trying to work out what packages are in the ARM repository, however the Ubuntu information seems very inconsistent.

For example:

One of my applications I use is "ensiper".   Now according to this:

[http://packages.ubuntu.com/jaunty/esniper](http://packages.ubuntu.com/jaunty/esniper)

And this:

[http://packages.ubuntu.com/search?keywords=esniper&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=esniper&searchon=names&suite=all&section=all)

It's only available for i386 and AMD64 arch.

However if  I download [http://ports.ubuntu.com/dists/jaunty/universe/binary-armel/Packages.gz](http://ports.ubuntu.com/dists/jaunty/universe/binary-armel/Packages.gz)

It shows that there is a ARM port of the esniper in there.

Which is correct?  Is there any way to get a DEFINITIVE list of what packages are available for jaunty ARM?

thanks.

---

### Post by dlmarti on 2009-08-01
I develop on ARM everyday (my job).
Never used Ubuntu on the ARM platform.

Even if no one has packaged esniper for ARM, its still an option to just download the package and compile it.

---

### Post by mgillespie on 2009-08-01
> **dlmarti said:**
> I develop on ARM everyday (my job).
Never used Ubuntu on the ARM platform.

Even if no one has packaged esniper for ARM, its still an option to just download the package and compile it.

The problem is with the Sheevaplug, is it's only got 512MB of flash, so I don't want to fill it up with compilers and libraries, I only want binaries and I don't want to go to the hassle of dross compiling either.

---

### Post by dlmarti on 2009-08-01
> **mgillespie said:**
> The problem is with the Sheevaplug, is it's only got 512MB of flash, so I don't want to fill it up with compilers and libraries, I only want binaries and I don't want to go to the hassle of dross compiling either.

you can NFS mount a full file system, in order to compile.

---

### Post by mgillespie on 2009-08-01
> **dlmarti said:**
> you can NFS mount a full file system, in order to compile.

To be honest, I am not looking at compiling anything on the Sheevaplug, it's not what it was bought for, and if I did want to compile, I would use my regular distro (Gentoo), which is a source based distro).  I have decided to switch to a binary based distro for my Sheevaplug, and hence looking for prebuild ARM binaries, hence my question about finding accurate info at to whats in the ARM repository.

Does anyone know?  Or have a place where I can ask Ubuntu ARM questions?   (it's supposed to be officially supported, but the support seems to be patchy, with all other architectues getting a IRC channel, and forums, and poor old ARM getting forgotten!!)

Should I be considering ditching Ubuntu on it when it arrives, and switching to something with more complete and active ARM support?

---

### Post by mgillespie on 2009-08-01
Looks like the package search is out of date, or does not include ARM port details, as esniper is indeed in the ARM tree.

[http://packages.debian.org/squeeze/armel/esniper/download](http://packages.debian.org/squeeze/armel/esniper/download)

> Package: esniper
Priority: extra
Section: universe/misc
Installed-Size: 136
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Dima Barsky <dima@dxxxebxxxiaxn.org>
Architecture: armel
Version: 2.19.0-1
Depends: libc6 (>= 2.4), libcurl3 (>= 7.16.2-1), libidn11 (>= 0.5.18), libkrb53 (>= 1.6.dfsg.2), libldap-2.4-2 (>= 2.4.7), libssl0.9.8 (>= 0.9.8f-5), zlib1g (>= 1:1.1.4), ca-certificates
Filename: pool/universe/e/esniper/esniper_2.19.0-1_armel.deb
Size: 40600
MD5sum: 40e4a796d12cfaa22fc7e7c3701d7db2
SHA1: 2f47de3729df689aa3d0f01829e8d5a0fc9e0d5c
SHA256: 2840b686eb907398315bd29e75196bff4ab76a5fd7ae1af8cca6276cf5babb78
Description: a simple, lightweight tool for sniping ebay auctions
 esniper is a lightweight ebay sniping tool. It doesn't have a lot of
 features, and that is by design.
 .
 Auctions  are  specified  on the command line, using the auction number
 and your bid price.  Multiple auctions can be bid on by specifying more
 auctions  and  bid prices.  esniper stops when the desired quantity has
 been won (default is 1).

---

