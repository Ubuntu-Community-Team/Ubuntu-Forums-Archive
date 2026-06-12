---
title: "How to configure grub2 to boot HaikuOS"
date: 2010-03-25
forum: General Help
---

### Post by LinScape on 2010-03-25
Hi, i installed ubuntu 9.10 for sometime now and i really like it.
It seems that ubuntu 9.10 comes with grub2 or some sort of grub beta and i want to install
HaikuOS but i dont know how to configure grub2 to boot up Haiku.
A simple guide would help.
Thank you ^^

---

### Post by oldfred on 2010-03-25
Not familiar with HaikuOS. What boot loader does it use grub legacy, grub2, lilo or other?

If you can install its boot loader to the partition boot sector then you can chainboot. A boot loader has to be in its partition not the MBR.
Grub2 with chainboot examples
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

Examples of 40_custom entry:
# Chainload another bootloader
menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

grub2 counts from 1 for partitions

# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd0,N)
    chainloader +1
}

Otherwise you have to know the exact entry from its menu.lst if old grub and convert to new grub style and add to 40_custom.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by LinScape on 2010-03-26
HaikuOs uses its own bootloader. [http://www.haiku-os.org/docs/userguide/en/bootloader.html](http://www.haiku-os.org/docs/userguide/en/bootloader.html)

---

### Post by oldfred on 2010-03-27
I totally do not understand all the details because I have not done it, but your have to makebootable to the partition you install to.
[http://haiku.mlotz.ch/](http://haiku.mlotz.ch/)

Then you can use the chainboot example above to boot into the partition where the boot file are.

---

### Post by LinScape on 2010-03-27
I think Haiku's Live CD installer makes the partition bootable automatically.

---

### Post by koki on 2010-03-30
> **LinScape said:**
> Hi, i installed ubuntu 9.10 for sometime now and i really like it.
It seems that ubuntu 9.10 comes with grub2 or some sort of grub beta and i want to install
HaikuOS but i dont know how to configure grub2 to boot up Haiku.
A simple guide would help.

Adding Haiku to GRUB2 in Ubuntu 9.10
[http://haikuzone.net/tips/installation/adding-haiku-grub2-ubuntu-9.10](http://haikuzone.net/tips/installation/adding-haiku-grub2-ubuntu-9.10)

Hope this helps!

---

### Post by LinScape on 2010-04-19
YES!!! thank you.

---

### Post by SirPecanGum on 2010-09-10
It did, thank you very much!

> **koki said:**
> Adding Haiku to GRUB2 in Ubuntu 9.10
[http://haikuzone.net/tips/installation/adding-haiku-grub2-ubuntu-9.10](http://haikuzone.net/tips/installation/adding-haiku-grub2-ubuntu-9.10)

Hope this helps!

---

