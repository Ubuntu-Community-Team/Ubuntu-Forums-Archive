---
title: "Creating a spare, module-less kernel"
date: 2006-02-06
forum: General Help
---

### Post by GetImOliver on 2006-02-06
Thanks in advance for all the help!
I want to create a spare Ubuntu 5.10 kernel! This kernel must:
1) be accessable from the GRUB bootloader.
2) have absolutely no unneccessary modules

I was thinking I could use the extra kernel installed with my 1st install:
Ubuntu, Kernal 2.6. 12-9-386

- Would this be an unwise decision? 
- Would changes here affect 12-10-386 at all?
- If it would be a better idea to just install a different kernal, how would I go   about doing so?
- How would I get that kernal on GRUB?

Anyways, after I have the spare kernel...
- How would I go about deleting all the modules? (save a graphics module)
- I know there was a terminal command to see a list of all modules and play around with them. Menu.config or something of that sort. What is the command to access this info to change it?

I'm sorry if these questions are too trivial/too many. Thanks very much for all your time and answers!

---

### Post by az on 2006-02-06
[QUOTE=GetImOliver]Thanks in advance for all the help!
I want to create a spare Ubuntu 5.10 kernel! This kernel must:
1) be accessable from the GRUB bootloader.
2) have absolutely no unneccessary modules![/QUOTE]

Great.  Recompile the kernel using kernel-package.  You will end up with an installable linux-image (or kernel-image) package that will act just like an ubuntu one.  When you install it, it will create a grub entry. When you remove it, it will remove the grub entry.

[QUOTE=GetImOliver]
I was thinking I could use the extra kernel installed with my 1st install:
Ubuntu, Kernal 2.6. 12-9-386

- Would this be an unwise decision? 
- Would changes here affect 12-10-386 at all?
- If it would be a better idea to just install a different kernal, how would I go   about doing so?
- How would I get that kernal on GRUB?[/QUOTE]
You can't really do that.  The vmlinuz image is really bare.  You will not be able to access your hard drive unless you load the ide modules, for example.  Your kernel boots with an initrd (a ramdisk that is put into memory by the bootloader)  The initrd contains the needed modules for booting.

If you remove modules, you would need to have them compiled as kernel options, so that this functionality is part of the vmlinuz image.  You cannot add something on to a precompiled linux kernel image.


[QUOTE=GetImOliver]

Anyways, after I have the spare kernel...
- How would I go about deleting all the modules? (save a graphics module)
- I know there was a terminal command to see a list of all modules and play around with them. Menu.config or something of that sort. What is the command to access this info to change it?

I'm sorry if these questions are too trivial/too many. Thanks very much for all your time and answers![/QUOTE]

Right now, type
lsmod
That will list all the modules you have loaded.  Look at the howto on copmiling the kernel using kernel package.  When you do menuconfig, just untick all of the options which are selected as modules except the ones listed by lsmod.  Select them as options (compiled into the kernel) and not as modules.  Good luck.

When all is said and done, you will have a .deb package of your statically-compiled kernel.  Install it and boot into it.

If it fails to boot (it will the first few dozen times) you can always boot into your older kernel and reconfigure and recompile it.

It's a great way to kill a weekend!

---

### Post by GetImOliver on 2006-02-06
That was just what I needed. Thanks again! Quick question though: when I lsmod, should I take into account the modules that are being used only by  "0"?

---

### Post by RAOF on 2006-02-06
[QUOTE=GetImOliver]That was just what I needed. Thanks again! Quick question though: when I lsmod, should I take into account the modules that are being used only by  "0"?[/QUOTE]
Yes.  These modules are still being used, just not by other **modules**.

---

### Post by GetImOliver on 2006-02-06
Alright, I was thinking that was the case. Why would they be listed otherwise? Oh well. 
I didn't want any USB support, so I disabled the gadgets in the make menuconfig. but when I go to compile the kernel I get:

CC      drivers/usb/gadget/ether.o
drivers/usb/gadget/ether.c: In function `eth_bind':
drivers/usb/gadget/ether.c:2510: error: `STATUS_BYTECOUNT' undeclared (first use in this function)
drivers/usb/gadget/ether.c:2510: error: (Each undeclared identifier is reported only once
drivers/usb/gadget/ether.c:2510: error: for each function it appears in.)
make[3]: *** [drivers/usb/gadget/ether.o] Error 1
make[2]: *** [drivers/usb/gadget] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2

I tried enabling the USB gadgets again, but essentially the same error appeared. Any ideas for getting around this? Once again, thank you all for the help!

---

