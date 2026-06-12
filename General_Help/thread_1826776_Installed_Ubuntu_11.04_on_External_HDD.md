---
title: "Installed Ubuntu 11.04 on External HDD"
date: 2011-08-17
forum: General Help
---

### Post by Chantian_Deanie on 2011-08-17
As the title says I installed Ubuntu on my External HDD. Windows 7 is installed on my internal HDD.

Neither Operating system will load unless the external is plugged in.

When I try boot without the external it says "Device long string of random letters and numbers could not be found" 

Then under it says 'Grub Rescue' and gives you the option to put commands in.

(This is on a black and white screen I think it's called a command line interface?)

The bad part is, my eternal is not USB powered. It wont be recognized by BIOS on start up. The only way for me to boot from it is after a restart it wont boot from a shutdown. The only way I can boot from the external after a shutdown is to boot from the Linux install cd first then reset from the installation wizard.


The above information^^ are the facts bellow I'll put my assumptions.

I assume the device grub refers to is my external HDD. I assume grub has over ridden my windows load manager.

The main OS I care about is windows. How can I make my computer boot windows without my external. I don't even care if I need to get rid of Linux, I have another computer I can single boot it from.

---

### Post by dolphin194 on 2011-08-17
I know what you have to do, but I have no clue how to do it.

Ubuntu uses a bootloader known as GRUB. Since GRUB is part of Ubuntu, you will need to have the external hard drive because your linux installation is on the external drive.

Change the bootloader to the Windows 7 loader, and add an option for ubuntu to it.

I had a similar problem before where I wanted to add Linux to the Windows 7 bootloader and use it. The result: I gave up because I couldn't find any information and formatted my hard drive.

If you can figure out how to do this, you should have no problem with your external hard drive.

---

### Post by Chantian_Deanie on 2011-08-17
Yeah lol. That's what I want to do ideally. Unfortunately I have no idea how to do it either. TBH I would be surprised if windows allowed you to add a Linux option to it's loader. They don't seem to be very Linux friendly.

I want to just remove Grub and hopefully the windows loader is still there behind it but I don't know how, and if it's not still there I would be screwed. Or even better would be if I could just set the windows loader as my default and not grub. Unfortunately I don't know if this is even possible? Surely someone here has done this (or something similar) before?

---

### Post by oldfred on 2011-08-17
You need to inistall the grub2 boot loader to the external drive, install a windows boot loader to the internal drive and reset grub's parameters so on updates it reinstalls to the correct drive.

You can do it separately but this walks you thru the process:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

