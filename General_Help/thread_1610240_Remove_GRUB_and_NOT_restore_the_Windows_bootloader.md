---
title: "Remove GRUB and NOT restore the Windows bootloader"
date: 2010-10-31
forum: General Help
---

### Post by MonkeyHood on 2010-10-31
Hi,

I've looked around the net and found many articles on how to remove GRUB but they all seem to be guides on replacing it with the standard windows boot loader.

Is there any way to simply remove grub?  Does GRUB reside in a specific partition?  Do I have to just delete the partition that has GRUB on it?


The way my bootable partitions work is something like this.
1)Installed Vista
2)Installed Ubuntu
3)Thought I removed GRUB
4)Put in new HDD(1) and installed Win7 onto it
5)Put in another new HDD(2) and put another Win7 onto that (but I disconnected every other HDD so that the bootloader would be written onto the new HDD(2).

When I have all my HDD's plugged in now, I get a GRUB load error (I think it's 21).

---

### Post by WorMzy on 2010-10-31
Changing the boot order of your disks is the best option. There is a way to wipe out your MBR, but there's not much point.

I'll leave this here anyway, use it at your own discretion. [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/]("http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/") (look at the second part of the tutorial, entitled "Using Linux".)

---

### Post by MonkeyHood on 2010-10-31
I can't believe I never thought of changing the boot order.  Thanks!

---

### Post by dcstar on 2010-11-01
> **MonkeyHood said:**
> Hi,

I've looked around the net and found many articles on how to remove GRUB but they all seem to be guides on replacing it with the standard windows boot loader.

Is there any way to simply remove grub?  Does GRUB reside in a specific partition?  Do I have to just delete the partition that has GRUB on it?
.........

Every system **needs** a bootloader (Grub, Windows, LILO, Syslinux whatever), without a bootloader it **cannot** boot.

You just cannot "remove" a bootloader.

---

### Post by MonkeyHood on 2010-11-01
I realize that.  The problem is, I had two bootloaders in one system.  I just wanted to get rid of the GRUB bootloader for now.

---

