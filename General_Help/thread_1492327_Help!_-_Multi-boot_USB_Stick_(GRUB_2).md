---
title: "Help! - Multi-boot USB Stick (GRUB 2)"
date: 2010-05-24
forum: General Help
---

### Post by Arokha on 2010-05-24
I've installed Ubuntu 10.04 on a sizable USB thumbdrive and left a 14gb ext2 partition at the end for various utilities to boot into. This is mostly a diagnostic kind of thing I'd be using it for and I'd like to be able to boot some other distros or tools such as Hiren's Boot CD and Backtrack Linux. I'd like to be able to either boot the installed Ubuntu, or other things of my choosing.

I understand what the bootloader is for, but don't have an in-depth understanding of the workings of GRUB. I'm in IT so I will pick up on any ideas people throw out quickly, most likely! Just tell me what I'd need to do. Do I need to extract the files from the ISO into that partition in folders named sensible things, or can the ISO somehow be mounted? That partition is sda5 by that naming convention... I guess that's hd0,4? Anyway... any help would be appreciated!

---

### Post by sundar_ima on 2010-07-10
> **Arokha said:**
> I've installed Ubuntu 10.04 on a sizable USB thumbdrive and left a 14gb ext2 partition at the end for various utilities to boot into. This is mostly a diagnostic kind of thing I'd be using it for and I'd like to be able to boot some other distros or tools such as Hiren's Boot CD and Backtrack Linux. I'd like to be able to either boot the installed Ubuntu, or other things of my choosing.

I understand what the bootloader is for, but don't have an in-depth understanding of the workings of GRUB. I'm in IT so I will pick up on any ideas people throw out quickly, most likely! Just tell me what I'd need to do. Do I need to extract the files from the ISO into that partition in folders named sensible things, or can the ISO somehow be mounted? That partition is sda5 by that naming convention... I guess that's hd0,4? Anyway... any help would be appreciated!


Hve a look at [**[COLOR="Red"]MultiBootUSB...[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1518273") thread

---

### Post by C.S.Cameron on 2010-07-10
MultiBootUSB +1

It's educational to review the grub.cfg file it produces.

---

### Post by oldfred on 2010-07-10
MultiBootUSB +1

I manually did what the multBootUSB does. Basically you install grub2 to the USB which if you have a full install to the USB you have done.
Then you edit grub.cfg to loopmount the ISO files. The biggest issue is figuring out the exact loopmount commands for each distribution. In the MultBoot script is just about every entry you would need but as a script it has the variables that you would supply earlier in the process. I have not tried the Multiboot script but it looks like an easy way to do it.

If you want to understand a little more of what it is doing some links to the manual way. Panticz is a script just to install a few specific ISOs.
MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands to install grub2.
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb](http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb)

---

