---
title: "Unetbootin - VFS cannot mount fs?"
date: 2012-04-19
forum: General Help
---

### Post by AlexOnVinyl on 2012-04-19
I've been trying to load mutliple Linux OS's off of USB thumbdrives using UNetbootin both 494 and UNetbootin 568 - I've tried Debian netinst and Live iso for i386 - Ive also tried loading up SLitas as well - and I keep getting the similar message when trying to load to Live mode - something about > Kernel Panic VFS unable to mount fs or something along the lines of that

is this a common bug with Unetbootin that is causing this.

Btw - I've used FAT formatted usb drives.  Nothing else.

---

### Post by kc1di on 2012-04-19
I'm not sure you can use netubootin for multiple booting. that being said this notice is found on their web page:

> UNetbootin doesn't use distribution-specific rules for making your live USB drive, so most Linux ISO files should load correctly using this option. However, not all distributions support booting from USB, and some others require extra boot options or other modifications before they can boot from USB drives, so these ISO files will not work as-is. Also, ISO files for non-Linux operating systems have a different boot mechanism, so don't expect them to work either.

Don't know which OS's your trying to boot but this may be the problem. Kernel panic sometimes happen when the kernel can't be found by the boot loader or the kernel can't find a module that it's supposed to load.

---

### Post by AlexOnVinyl on 2012-04-20
> **kc1di said:**
> I'm not sure you can use netubootin for multiple booting. that being said this notice is found on their web page:



Don't know which OS's your trying to boot but this may be the problem. Kernel panic sometimes happen when the kernel can't be found by the boot loader or the kernel can't find a module that it's supposed to load.

**Update: I've made my way into using Multiboot USB instead of Unetbootin - so the rest goes as follows:**

I'm trying to dual Boot Ubuntu being my 1st Primary OS and Debian as a secondary - recovery - I've already formatted my Drive and partitioned it for enough space - as you can see here:

[IMG]http://i.imgur.com/elDsa.png[/IMG]

Am I supposed to format the Unallocated space as EXT or do I leave it Unallocated for the OS to decide to format it?

---

### Post by flurospar on 2012-04-20
> **AlexOnVinyl said:**
> Am I supposed to format the Unallocated space as EXT or do I leave it Unallocated for the OS to decide to format it?

You can do both of them, though I would have done the former.

---

### Post by dcukfoptjdu on 2012-04-20
[Tory Burch Heels](http://www.toryburchdesigner.com/shoes-tory-burch-heels-c-195_203_214.html)

---

### Post by AlexOnVinyl on 2012-04-20
> **flurospar said:**
> You can do both of them, though I would have done the former.

I just tried use Multiusb and Unetbootin to try and run a live cd of SLiTaz - it gave me back the infamous > trying to unpack rootfs image as initramfs then it hangs.  My computer has 3GB of ram and is a dual processor - do you think this is just a result of a bad setup of the iso? or something worse?


ALSO: I did manage to get Kanotix to work - would that be good enough to use as say a recovery distro incase if my Ubuntu goes down?

---

