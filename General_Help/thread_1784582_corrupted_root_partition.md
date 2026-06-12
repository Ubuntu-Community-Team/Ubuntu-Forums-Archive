---
title: "corrupted root partition"
date: 2011-06-17
forum: General Help
---

### Post by camaron1 on 2011-06-17
Windows/ubuntu install. I can access grub but wont boot into ubuntu. I have separate root and home partitions. Root seems to be corrupted. I initially managed to boot from live cd but I can't any more. So I'm totally stuck. Error when trying to boot from live cd:


> stdin: error 0
Segmentation fault
unable to open /dev/sda
stdin: error 0

I need suggestions please...

---

### Post by iandunham on 2011-07-10
I have this exact same problem! How did you solve it?

---

### Post by iandunham on 2011-07-10
I have this exact same problem! How did you solve it?

---

### Post by Blasphemist on 2011-07-10
The error is referring to the hard drive and don't be too surprised if it's toast but on the other hand don't give up. I think the bios must be set to try and boot from the hard drive first and not the cd. You can change that by pressing whatever F key you see it post when you first turn it on. Many pc's also give you an option to press a different key to access a boot menu and you could use that. If you do, you'll get a list of devices to boot from and you could choose the cd, or a usb if you have a bootable usb.

If by some chance the hard drive is toasted, a bad physical or electronic failure, I suppose it could keep you from getting to this point of choosing a different boot device or order. I think you could eliminate that possibility by removing the hard drive and choosing to boot to the cd or usb. I don't think you'd get to where you are if the bios was hosed.

This should allow you to boot to the cd or usb. What you can do then depends on what bootable cd or usb you have. An Ubuntu Live cd or usb would allow you to get back to this thread and you'd be able to run GParted to see the partitions. You could take a screen shot from GParted and post it here. There is a boot info script you could run and post the results that would tell us more. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

There are numerous other utility iso's you can burn to disc such as system rescue cd [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) , test disk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) and others. Without knowing more about your specifics I can't recommend one specifically or tell you just what to do. Hopefully this helped move you forward. Please post back what you can about what has happened from using this and as much detail about your system as you can.

---

