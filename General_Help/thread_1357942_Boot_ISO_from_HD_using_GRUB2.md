---
title: "Boot ISO from HD using GRUB2?"
date: 2009-12-17
forum: General Help
---

### Post by TheForkOfJustice on 2009-12-17
I'm trying to save CD-R media and would like to know how to mount a partition (or ISO image) as if it were a CD drive so I can boot LiveCDs from it and install linux distros on another partition on the same hard drive.

I'll need to know how to edit GRUB2 for this task with a custom entry, too. Old instructions for GRUB1 probably wont do the trick.

Thanks in advance.

---

### Post by synapsys on 2009-12-17
Are CD-R's really that expensive in your area?

You could always make a bootable thumb drive from your iso, that way it would be reusable....

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by northern lights on 2009-12-17
> **TheForkOfJustice said:**
> I'm trying to save CD-R media and would like to know how to mount a partition (or ISO image) as if it were a CD drive so I can boot LiveCDs from it and install linux distros on another partition on the same hard drive.
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") - same principle, way relaxed.

Instructions on the site should suffice.

Also available from the repos, but not with a 9.10 installer, so download the binary from the website.

---

### Post by rahilm on 2009-12-17
Unetbootin as the above posts suggests is the answer. Booting an iso the grub2 way is a big headache, not because it is tough , but because every linux distribution has its own unique way of booting and you'll have to research for every iso you download, and there is no telling it will work.

Like, i managed to boot ubuntu 9.10,9.04,8.04, Puppy linux 4.21, Qimo(ubuntu again), but dsl just refuses to boot.

---

### Post by Matt Yun on 2009-12-17
I agree with the Unetbootin answers above.  However, just to be thorough, you can actually boot from *.iso files using USB flash drives.  It's not easy, however, for most [Linux distros that require protected mode kernel drivers.]("http://diddy.boot-land.net/grub4dos/files/map.htm#hd32")

Here is a tutorial from [pendrivelinux.com]("http://pendrivelinux.com"):  [Boot ISO from USB Flashdrive]("http://www.pendrivelinux.com/boot-iso-from-usb-flash-drive/") and [Boot Multiple ISO from USB (Multiboot USB)]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/").

---

### Post by efflandt on 2009-12-17
Actually if you have any existing Ubuntu system, it is easy to create a bootable USB device with any Ubuntu related iso.  It is System > Administration > USB Startup Disk Creator.  So it works as well for Linux Mint, Qimo, etc.

But I recently bought packs of 10 CD's for $2, which is 20 cents each.

---

### Post by Bluesman77 on 2009-12-18
Maybe the objective of this post is to contaminate less by burning fewer CD´s, rather than to save $2.

I tried to do the same by editing the /boot/grub/grub.cfg (although it´s not recommended) using*loopback*, but i still can´t do it...

---

### Post by TheForkOfJustice on 2009-12-18
> **Bluesman77 said:**
> Maybe the objective of this post is to contaminate less by burning fewer CD´s, rather than to save $2.

I tried to do the same by editing the /boot/grub/grub.cfg (although it´s not recommended) using*loopback*, but i still can´t do it...

Correct.  Going through CD-Rs that I may not need is WASTEFUL and should be avoided. Just doing my part for the environment by creating less garbage.

As mentioned earlier I'll try Unetbootin or the USB thing in Ubuntu but I'm pretty sure I can't boot from USB on my system.

---

### Post by Jose Catre-Vandis on 2009-12-18
This link might help

[http://ubuntuforums.org/showthread.php?t=457318](http://ubuntuforums.org/showthread.php?t=457318)

Check my post (#50?) regarding grub2

---

