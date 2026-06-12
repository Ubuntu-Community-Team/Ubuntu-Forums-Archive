---
title: "linux kernel 2.6.32 update ?"
date: 2009-12-04
forum: General Help
---

### Post by peakpc on 2009-12-04
How long does it usually take to for Ubuntu to incorporate the next released kernel. I am hoping that kernel 2.6.32 will fix my resume woes.

---

### Post by arubislander on 2009-12-04
Usually the next released kernel is incorporated into the next coinciding release of Ubuntu, in this case Lucid Lynx... it is not usual that the current version of Ubuntu gets upgraded to a new kernel. Patch to the existing kernel are applied though.

---

### Post by peakpc on 2009-12-05
well I just got the update to 2.6.31-16 now I've seen -14,-15 and now -16 with no help to the ati drivers that I believe is causing the blank screen on resume for many people.  For me this is not enough to regress to 9.04 but, it is a glaring issue.

---

### Post by arubislander on 2009-12-06
I guess unless someone backports the relevant code to the 2.6.31 kernel you'll either
1. have to patiently wait till april 2010 and not use suspend / hibernate in the meantime...
2. Hunt around for a ppa with the 2.6.32 kernel or
3. compile the 2.6.32 kernel yourself.

I'd go with option number 1 though...

---

### Post by fooman on 2009-12-06
i have installed the 2.6.32 kernel from the PPA ....it is simple to do and is working fine for me.  here is the link:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

you will need 3 packages from the kernel version that you choose (the final 2.6.32 kernel has the release date of 03-Dec-2009)....download:

1)linux-headers-2.6.32-020632_2.6.32-020632_all.deb
2)linux-headers-2.6.32-020632-generic_2.6.32-020632[COLOR=Red]**either i386 or amd64**.deb[/COLOR] ...depending on which architecture you are using 
3)linux-image-2.6.32-020632-generic_2.6.32-020632[COLOR=Red]**either i386 or amd64**.deb[/COLOR] ...depending on which architecture you are using 

they are .deb files so you should be able to just double-click on them to install.

**IMPORTANT:  be sure to install them in the same order that i put them in above!!

hope that helps.

---

### Post by foxy123 on 2009-12-06
I have installed the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), but it does not boot, I have just a black screen and nothing afterwards. BTW,  tried to compile it myself with the same result. I wonder what may cause it. I used to compile the kernel before and it worked fine.

---

### Post by hechacker1 on 2009-12-08
I have 855gm hardware too, and it broke with 2.6.32. There is something wrong with kernel mode setting and ACPI.

If you use the 2.6.32 kernel with acpi=off boot parameters then my laptop's display doesn't go black during KMS initialization.

Unfortunately without ACPI I don't have any power management.

I've gone back to 2.6.31 myself until this bug is fixed.

---

### Post by foxy123 on 2009-12-08
> **hechacker1 said:**
> I have 855gm hardware too, and it broke with 2.6.32. There is something wrong with kernel mode setting and ACPI.

If you use the 2.6.32 kernel with acpi=off boot parameters then my laptop's display doesn't go black during KMS initialization.

Unfortunately without ACPI I don't have any power management.

I've gone back to 2.6.31 myself until this bug is fixed.

I have put "nomodeset" parameter and was able to boot without any problem. The kernel did not though fix my problem with rt2500 driver :(

---

### Post by Redsunz on 2009-12-18
> **foxy123 said:**
> I have put "nomodeset" parameter and was able to boot without any problem. The kernel did not though fix my problem with rt2500 driver :(

Could you please but that in newbie terms? :)
I have no idea what that means. ""nomodeset" parameter"
Do you have to edit a particular file?
I got the Kernel to update and was very excited as my sound problem had been resolved.
But on the Second reboot it would no longer start just a black screen.
Thankfully after a couple failed boots it came up with the options to boot into my older Kernel and then I was able to uninstall the new kernel via the Synaptic Package manager.

---

### Post by Redsunz on 2009-12-18
Never mind "nomodeset" parameter"
I figured that out however it still does not boot a second time with the new kernel.
I get this error 
Target filesystem doesn't have /sbb/init
No init found.  Try passing init=bootarg.

Does any one know what this means and why my machine won't boot with the new kernel?

Thanks

---

### Post by Redsunz on 2010-02-13
> **Redsunz said:**
> Never mind "nomodeset" parameter"
I figured that out however it still does not boot a second time with the new kernel.
I get this error 
Target filesystem doesn't have /sbb/init
No init found.  Try passing init=bootarg.

Does any one know what this means and why my machine won't boot with the new kernel?

Thanks

Okay its finally working now!! After updating the Kernel my machine would lock up.  I booted from the Ubuntu cd and ran Gparted and did a check on  /dev/sda1 now its working! Im not sure why I had this problem and others did not maybe it's caused by using a solid state disk?
:D

---

