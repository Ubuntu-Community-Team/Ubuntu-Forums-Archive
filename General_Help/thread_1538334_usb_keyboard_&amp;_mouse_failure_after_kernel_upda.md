---
title: "usb keyboard &amp; mouse failure after kernel updates in 10.4"
date: 2010-07-24
forum: General Help
---

### Post by b3nw on 2010-07-24
Linux 2.6.32-22 is the last kernel that works for me on 10.04. After the 23 upgrades when I boot I make it to my login screen but my keyboard and mouse do not work. I hoped that this was a fluke bad release and waited for version 24. Unfortunantly that was released recently and did not fix the problem.

Linux desktop.ben.io 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Since neither work I have no real way to provide any debugging info or details. 

My only solution currently is to manually select or set as default the -22 kernel.

So my question is, how/what information should I provide to make a bug report on this or does anyone know of this problem or a way around it (my searches came up with nothing as the terms were too generic).

Thanks

---

### Post by dcstar on 2010-07-25
> **b3nw said:**
> Linux 2.6.32-22 is the last kernel that works for me on 10.04. After the 23 upgrades when I boot I make it to my login screen but my keyboard and mouse do not work. I hoped that this was a fluke bad release and waited for version 24. Unfortunantly that was released recently and did not fix the problem.

Linux desktop.ben.io 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Since neither work I have no real way to provide any debugging info or details. 

My only solution currently is to manually select or set as default the -22 kernel.

So my question is, how/what information should I provide to make a bug report on this or does anyone know of this problem or a way around it (my searches came up with nothing as the terms were too generic).

Thanks

People experienced a similar problem with VMware Player VMs in 10.04 which was eventually traced to an incorrect setting, so you may want to try this:

[http://ubuntuforums.org/showpost.php?p=9145816&postcount=4](http://ubuntuforums.org/showpost.php?p=9145816&postcount=4)

---

### Post by b3nw on 2010-07-31
My host is running Ubuntu 10.4 (64bit) and after the last 2 kernel updates the keyboard and mouse do not work, not a guest VM.

That said, I did try all the workarounds in that post and on the related vmware link, no joy.

---

### Post by worksofcraft on 2010-07-31
I had to enable USB Keyboard and USB mouse support in my computer BIOS setup. (Note: I also enabled Legacy USB storage but have no idea what that is for).

BIOS settings are not standard, but on my computer I press Del key to enter setup as soon computer powers on. Then they are in Advanced settings...

---

### Post by b3nw on 2010-07-31
The keyboard and mouse worked in previous kernel versions and it works in the boot menu.... it also works in Windows 7/XP ect when booted into that. I don't see how a bios change would fix this?

I'm staying prior 2 the last two kernel versions, everything worked fine (and still does, if I boot into the old kernel version).

---

### Post by worksofcraft on 2010-07-31
I think some boot loaders and operating systems have USB support built in and others rely on the BIOS to do it for them.

The latter  makes them more efficient, especially when you don't have a USB keyboard and mouse :shock:

Historically people had to add a separate USB card to their computers and there was no support for it in the BIOS so Windows and GRUB Legacy both built this functionality into their products. 

I suspect in later Ubuntus they decided it was redundant but until you turn it on in your BIOS we won't really know ;)

p.s. It could be Grub2 or the keyboard/mouse drivers or the Kernel... IDK any one of those might have lost their integral USB support to depend on the BIOS.

---

### Post by b3nw on 2010-08-01
- there was no options for USB support in my bios, this comp is new enough I assume it is always on

- my keyboard and mouse DO work in grub

- my keyboard in mouse FAIL after either 2.6.32-23 or 2.6.32-24 is booted, the last working version is 2.6.32-22.

This *IS* a kernel issue, nothing more. I am trying to figure out how to get information on how to report it, or fix it if it is specific to my system (Dell Studio Slim 540s)

---

### Post by worksofcraft on 2010-08-01
OK well IDK if this information helps:

When I first started using USB keyboard, Windows XP worked, but Ubuntu received no mouse or keyboard events.

I could not even use the USB keyboard to enter BIOS setup and had to connect up my old keyboard to find the setting under "integrated peripherals" (not under "advanced settings" as I stated previously by mistake).

I am now running 2.6.32-24-generic 64 bit on AMD quad core with a Logitec wireless keyboard and mouse connecting thru USB wireless adapter and it all has been working fine for me!

---

