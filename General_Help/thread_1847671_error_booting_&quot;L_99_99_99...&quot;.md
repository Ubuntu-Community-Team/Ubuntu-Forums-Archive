---
title: "error booting &quot;L 99 99 99...&quot;"
date: 2011-09-21
forum: General Help
---

### Post by argie01 on 2011-09-21
Hi,

I have an Ubuntu 7.10 installed on a PC with 3 hard disk.
After a crash of the power supply unit, when the computer boots, after the POST, I get the error message

> L 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 

on the screen, and the computer halt.

So, I boot using an Ubuntu 9.10 live cd, and when I select the option "boot from first hard disk" the computer boots OK.

Then I got login as root, and I run the command 

> grub-install /dev/hda

this returned:

> (hd0) /dev/hda
(hd1) /dev/hdb

And that' all. After reboot I still have the error "L 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99".

Thank you for your help.

---

### Post by dcstar on 2011-09-22
> **argie01 said:**
> Hi,

I have an Ubuntu 7.10 installed on a PC with 3 hard disk.
After a crash of the power supply unit, when the computer boots, after the POST, I get the error message
.........

Make sure the BIOS is set to boot off the correct hard disk and use this:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

