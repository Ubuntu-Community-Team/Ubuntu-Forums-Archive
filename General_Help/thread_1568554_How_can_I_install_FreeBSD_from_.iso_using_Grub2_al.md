---
title: "How can I install FreeBSD from .iso using Grub2 along Ubuntu?"
date: 2010-09-05
forum: General Help
---

### Post by the8thstar on 2010-09-05
I want to install FreeBSD (PC-BSD) alongside Ubuntu 10.04 and Windows 7. I do not have a CD or a DVD or a USB key to burn the .iso, so I was thinking instead of using Grub2 to launch it.

I created an empty partition where FreeBSD will be installed (see screnshot below).

Now, where should I locate the .iso file? On my root partition? On my home partition? On the new partition (ZFS formatted)? Does it matter?

How should I set up my Grub2? I was thinking of adding this to /etc/grub.d/40_custom (if the partition where the .iso is located is /Home):

> menuentry "FreeBSD" {
insmod loopback
insmod iso9660
set isofile="~/iso/PCBSD8.0-x86-DVD.iso"
loopback loop (hd0,1)$isofile
}

Is it correct... and enough info?

---

### Post by perspectoff on 2010-09-05
Each of my computers has about 4 OSs on them. This includes Windows, Mac OSX, BSD (which I have used for about 7 years as a name server), and multiple variants of Ubuntu.

They never bump into each other.

Here's what I did:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

or

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

---

### Post by oldfred on 2010-09-05
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

Boot ISO from harddrive. To install it would have to be different partition
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

