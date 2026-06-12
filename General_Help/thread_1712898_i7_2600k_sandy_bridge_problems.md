---
title: "i7 2600k sandy bridge problems"
date: 2011-03-23
forum: General Help
---

### Post by plvt_florian on 2011-03-23
Hi
i have recently bougth this processor (Intel® Core i7-2600K SandyBridge, 3400MHz, 8MB, socket 1155), 8gb ram (Mushkin 8GB (2x4GB) PC3-10666 1333MHz ) , main board (Gigabyte PH67A-UD3-B3, socket 1155) and hard disk ( Western Digital Caviar Blue, 1TB, 7200rpm, 32MB, SATA 3 ) i have tried the latest version of ubuntu 10.10 64 bits and the problem is that it does not want to load. i reace the step to try or intall ubuntu and if i select something it is just loading forever. i mention that other operating sistem works ok (vista, xp,win7)
 
please help me out
 
thanks in advance

---

### Post by oldfred on 2011-03-23
Phoronix has been testing several of the sandybridge chips. Today they posted this on the i3 but the comment I think applies to all sandy bridge chips. What video are you using.


[http://www.phoronix.com/scan.php?page=article&item=intel_corei3_2100&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei3_2100&num=1)
The big caveat though is if using the Sandy Bridge graphics where you need to  be using the unreleased Ubuntu 11.04 or Fedora 15 for "out of the box"  support or otherwise be building the Linux 2.6.37/2.6.38 kernel, Mesa 7.11-devel,  and xf86-video-intel 2.14 from source or be using a third-party package repository  for these key components.

See also this review on the i5 which also discusses issues.
[http://www.phoronix.com/scan.php?page=article&item=intel_corei5_2500k&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei5_2500k&num=1)

---

### Post by plvt_florian on 2011-03-23
i have ati radeon hd 4800 series

---

### Post by oldfred on 2011-03-23
Then you may be able to try some video settings to boot. At liveCD, you see two icons, a keyboard & human. press any key, then try f6 for settings. Often nomodeset works but it may be this radeon.modeset=0.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

