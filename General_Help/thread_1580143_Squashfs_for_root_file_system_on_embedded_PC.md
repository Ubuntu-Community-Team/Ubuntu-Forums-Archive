---
title: "Squashfs for root file system on embedded PC"
date: 2010-09-22
forum: General Help
---

### Post by zaroff on 2010-09-22
Hello all,

Recently, I've been tasked with getting Ubuntu up and running on one of these:

[http://www.eurotech.com/en/products/embedded+boards/pc104+cpu+modules/ISIS]("http://www.eurotech.com/en/products/embedded+boards/pc104+cpu+modules/ISIS")

I've been able to spend some time with a development kit for it recently and it's a neat little system. My big problem at the moment is that the units I'll be working with only have a 1.9GB SSD drive. A clean install of Ubuntu Netbook takes up about 2.2GB and even if you remove a couple of the large packages like OpenOffice and ubuntu-docs, it's still an uncomfortably close fit on that little SSD drive. There definitely wouldn't be any room left for additional software that may needed later.

I was thinking perhaps a root file system based on squashfs might be a way to squeeze some more usable space out of the drive. There are a lot of howto's and tools around for customizing live cd's and RAM booting that make use of squashfs but nothing quite like I was thinking of implementing.

I was thinking of a procedure that might go something like this:
1.) Plug in a USB large enough to accommodate a full clean install of Ubuntu Netbook.
2.) Install to the larger external drive.
3.) Convert the install on the external drive to squashfs.
4.) Copy squashfs install to smaller onboard SSD drive.
5.) Make squashfs system bootable with GRUB.
6.) Add persistent home directory for the few files that will need to be saved between reboots.

Are there any procedures around that are anywhere close to this? Like I said I've found a lot of stuff about customizing live CDs but that's not quite what I want to do here. Any ideas?

---

