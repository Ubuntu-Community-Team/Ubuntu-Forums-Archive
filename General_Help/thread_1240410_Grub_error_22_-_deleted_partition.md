---
title: "Grub error 22 - deleted partition"
date: 2009-08-14
forum: General Help
---

### Post by Pete Zafase on 2009-08-14
Hi, I had a problem with my original ubuntu boot, so I made a dual boot with two ubuntu partitions, so I could use the other one while fixing sda1.
When I had fixed sda1, I had no need for sda2 anymore. I went into the partition editor, and deleted sda2. But when I boot now I get this:
Loading grub... Please wait.
Error 22

And then it won't boot.
Can someone please help me?
Btw, I am pretty noob on Ubuntu.

---

### Post by Pete Zafase on 2009-08-14
Please help me. The only thing I can do is to boot from the live cd.

---

### Post by stlsaint on 2009-08-14
you deleted your Grub which is what boots your system...use livecd to reinstall Grub!

---

### Post by Pete Zafase on 2009-08-14
I thought I just deleted the one partition.
So just download from the live cd again?

---

### Post by michy99 on 2009-08-14
How to fix grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Pete Zafase on 2009-08-14
Ahh thanks!
I did see the first part of the guide, but the second did help me!

But if I am going to try out other distros, and dual boot, how am I suposed to remove the one I don't want anymore then?

---

### Post by soapBAR2 on 2009-08-14
> **Pete Zafase said:**
> Ahh thanks!
I did see the first part of the guide, but the second did help me!

But if I am going to try out other distros, and dual boot, how am I suposed to remove the one I don't want anymore then?

Either boot onto the distro you DO want, and delete the one you don't want using a tool like gparted (GUI) or parted (CLI) / fdisk (CLI) / mkfs (CLI) / whatever. Then, if grub doesn't automagic, edit /boot/grub/menu.lst, and delete the entries for the deleted partitions (should be at the bottom). Or, don't edit it, and the next time the kernel updates, grub should automagic them out (you might be given the option to keep your old menu.lst or replace it).

If you're just trying out distros, I'd recommend a virtual machine platform like virtualbox. If you've used WUBI, you'll be familiar with the idea of "a computer within a computer" concept (although WUBI is an emulation/port rather than a virtual machine IIRC). It has several advantages:
- You don't have to risk your current install
- Uninstalls are really easy (just delete the virtual machine and the disk)
- The amount of disk space taken up is dynamic (ie, if you install 3.2gb worth of stuff on your new distro, you'll only lose 3.2gb of disk space, rather than having to partition off 8gb which you can't easily use from your main distro)
- No hardware hassles (all the hardware is virtual and mostly generic)

However, the disadvantages are
- You have to boot into your main system
- No accelerated graphics (ie, no compiz)
- Extra resources taken up (mainly because you're running 2 systems at once, plus a small VM overhead)
- Your virtual machine will not be as powerful as your main machine (because you have to set upper limits on things like memory/disk/video ram usage).

---

### Post by Pete Zafase on 2009-08-14
Thanks, I'm going to try out VirtualBox in the future!

But I did use GParted to delete sda2!

---

