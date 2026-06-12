---
title: "Clonezilla fails after bios upgrade"
date: 2011-07-19
forum: General Help
---

### Post by EngDrewman on 2011-07-19
I recently set up a Clonezilla server as I have 200+ computers to reimage. Everything was setup and working fine, until I ran into a computer that has a newer BIOS. Grub loads and works fine, but the kernel hangs.

Specs: 
Server: Dell OptiPlex 740
Ubuntu 10.10 Desktop x32, kernel 2.6.35-30 generic
Clonezilla version: 2.3.8-32
Amd Athlon 64 x2
1GB ram
bios rev 1.1.3

Failing client: Dell OptiPlex 740
OS: XP pro sp3 x32
All hardware identical to server
bios rev 2.2.5

So as mentioned above when I boot the client from PXE to image it, Grub loads, and as it tries to boot, the following lines appear:

Loading vmlinuz-pxe....
Loading initrd-pxe.img.....ready.
Probing EDD (edd=off to disable)....ok
[screen flickers then returns to the above text. Freezes.]

I updated the bios on a machine that previously worked to confirm/replicate the problem. How do I fix this?

edit: tried disabling EDD in grub's boot parameters- no change

---

### Post by SteveDee on 2011-07-21
> **EngDrewman said:**
> ...I updated the bios on a machine that previously worked to confirm/replicate the problem...

I have experience re-imaging systems on a Windows network using Fog, but have only used Clonezilla to re-image individual machines.

My first suggestion would be to determine whether this is a Ubuntu/bios compatability problem or an imaging/bios compatability problem.

So (if you haven't already done so) manually install Ubuntu on the problem machine and verify that it runs OK.

If the problem is still there after a manual install, you could try using the latest kernel.

If this problem is only apparent when re-imaging, you should try changing BIOS settings, especially options relating to the hard disk interface. (For example when using Fog, on some HP laptops I have to set "HDD Translation Mode" to "LBA-assisted").

In Fog you can specify Kernel Arguments, and it is sometimes necessary to use this feature (e.g. setting "acpi=force irqpoll") but I don't know what options you have available in your Clonezilla Server setup.

The "Probing EDD" text may not be indicating your problem (see: [http://www.linuxquestions.org/questions/linux-hardware-18/probing-edd-message-at-boot-time-what-does-it-mean-750715/](http://www.linuxquestions.org/questions/linux-hardware-18/probing-edd-message-at-boot-time-what-does-it-mean-750715/))


EDIT: I know this is Fog info (not Clonezilla) but may be useful: [http://www.fogproject.org/wiki/index.php?title=Talk:Dell_Optiplex_740](http://www.fogproject.org/wiki/index.php?title=Talk:Dell_Optiplex_740)

---

