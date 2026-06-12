---
title: "Lost printing capability, Ubuntu 10.10"
date: 2011-11-06
forum: General Help
---

### Post by Bobrm2 on 2011-11-06
Have been searching the forums and located a similarity between my problem and the printing problem by some that are using 11.10. 
  This is some of what I've found out:

bob@Ubuntu:~$ sudo update-grub
[sudo] password for bob: 
Generating grub.cfg ...
Found memtest86+ image: /memtest86+.bin
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
done
bob@Ubuntu:~$ 
 The error messages are:
 "There was an error sending document (job 308) to the printer.

  2. HP officejet J4680 series, HPcups 3.11.10.

  3. State is enabled. 

 This is an attempt to reconnect wirelessly, as it was before I upgraded from 10.04 to 10.10.

  The System/printing sees "Local Host".

Your help appreciated.

Bob

---

### Post by Bobrm2 on 2011-11-06
IN System/administration/printing, under policies "Enable" will not stay checked. The queue is not enabled, or isn't allowed to enable?

---

