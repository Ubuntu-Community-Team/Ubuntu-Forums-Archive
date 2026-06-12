---
title: "Installing (K)ubuntu on USB with partition for windows files"
date: 2012-04-02
forum: General Help
---

### Post by Fwission on 2012-04-02
Ok, so I want to install Ubuntu onto a usb stick while keeping at least 1 or 2 gigabytes left for an empty partition that windows can detect.

The problem is installing ubuntu manually won't create a boot loader, and using start-up disk (or any automatic installer) creates a buggy ubuntu that doesn't detect driver updates.

Any solutions?

---

### Post by sanderj on 2012-04-02
Take a USB-stick with FAT filesystem.
Boot Ubuntu (from harddisk or live-CD), and start usb-creator-gtk and let it create a persistent Ubuntu on the stick. With the slider in the first screen of usb-creator-gtk you can say how much space Ubuntu should take (and thus how much you leave to Windows).

NB: You should *not* do a normal Ubuntu installation to an USB stick; it will be very slow to run.

HTH

---

### Post by oldfred on 2012-04-02
I have a full install of 12.04 and had 10.10 on my 16GB flash drive with 8GB for / (root). I would not call it speedy nor as fast as hard drive especially loading a larger program and install is a lot slower as writes are the biggest issue with flash drives. But it is functional.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

If you want part of the flash to work with Windows make the first partition FAT32 as Windows only sees the first flash drive partition.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by HiImTye on 2012-04-03
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
use 'method 0'
if you want a storage partition then add a third partition in GParted. here is how I have mine set up:

1: FAT32: Ubuntu LiveUSB: >1GB (just large enough to store it)
2: EXT4: 'casper-rw': 4GB
3: FAT32: storage: 11GB

this gives me the benefits of ext4's speed for the persistent image and also the versatility of a storage drive for files that I share between devices (DivX files I use on my BluRay player, for instance)

---

