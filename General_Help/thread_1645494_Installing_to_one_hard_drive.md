---
title: "Installing to one hard drive"
date: 2010-12-14
forum: General Help
---

### Post by mike1357 on 2010-12-14
Hello all, my name's mike I'm new here.

I just made a live cd for 10.10 ubuntu/linux and I want to install just on one hard drive.  I read many places how to do this, but I'm looking for a little clarification.

2nd hard drive (D) is a 120 gb western digital, I run it off a PATA cable as slave to my cd drive.

My regular drive (C) is the seagate 160gb runs off the SATA at position 0.  This has my windows and drives etc.


I tried loading up the live cd after taking out the C drive and I soon found that I'm an idiot and the live cd can't run without the graphics card driver on my C drive (the stock radeon x300).  Can I get around this by downloading the driver to my D drive so I can use the computer completely without the C drive?  How so if I don't have the original back up disks?  (When I upgrade to a new graphics card I'll download the driver to both hard disks)


So I'm now in the live cd with both hard drives in, installing, and I get to the point in the installation that says "Allocate drive space".   This is where all the other posts or installation tutorials fall short.

Please help me with directions to just install on my D drive without wiping any files off the C drive.  Is it as simple as choosing "install alongside other operating systems" and then chosing "Use entire disk" for the secondary hard drive??

My biggest question is, if I select that option will it automatically partition any of the C drive and then I lose files?  How do I ensure manually that my C drive has no partitions and I use all of the D drive?


Thanks!!!
:popcorn:(I have more questions about virtualization with separate hard drives but I'll ask those later)

---

### Post by mike1357 on 2010-12-14
finally found what I was looking for-

[http://ubuntuforums.org/showthread.php?t=156785](http://ubuntuforums.org/showthread.php?t=156785)

---

### Post by 3rdalbum on 2010-12-14
> **mike1357 said:**
> 

I tried loading up the live cd after taking out the C drive and I soon found that I'm an idiot and the live cd can't run without the graphics card driver on my C drive (the stock radeon x300).  Can I get around this by downloading the driver to my D drive so I can use the computer completely without the C drive?  How so if I don't have the original back up disks?  (When I upgrade to a new graphics card I'll download the driver to both hard disks)


So I'm now in the live cd with both hard drives in, installing, and I get to the point in the installation that says "Allocate drive space".   Please help me with directions to just install on my D drive without wiping any files off the C drive.  Is it as simple as choosing "install alongside other operating systems" and then chosing "Use entire disk" for the secondary hard disk?

Yes, that is exactly what to do. The first hard disk (Windows drive letters have no meaning here) should be plugged in too, so the bootloader ends off on this drive. The bootloader will not damage your data on the first hard disk.

The Windows graphics driver is useless on Ubuntu, of course. Actually, Ubuntu includes a driver that works with your card - are you getting a blank screen or something? Have you tried pressing a key on the keyboard when you get the "man with many arms" on the screen, and then use the "Alternate boot options" on the screen that appears after that?

---

