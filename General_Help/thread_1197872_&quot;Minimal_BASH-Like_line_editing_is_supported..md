---
title: "&quot;Minimal BASH-Like line editing is supported...&quot; message on start up"
date: 2009-06-26
forum: General Help
---

### Post by chris_castro on 2009-06-26
My Ubuntu 9.04 is getting this message while trying to boot:

"[ Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]"

and Ubuntu wont load. Ubuntu is my only OS on that computer and my linux skills are quite rudimentary so I have no idea what to do.

I appreciate any suggestions,
Chris

---

### Post by maheshasolkar on 2009-06-26
This looks like a GRUB message. Did you change your system in any way, that it resulted in this message? Did you install windows or other OS? Changed partitions on your disk?

Which version of Ubuntu are you running?

---

### Post by chris_castro on 2009-06-26
A friend gave the computer to me,cause he couldn't seem to get it to work. so he said if i could soem how fix it i could keep it.  It is running Ubuntu 9.04.  It tried to reinstall it but it wont even boot off the disc just goes to a black screen ...please help

---

### Post by calrogman on 2009-06-26
> **chris_castro said:**
> A friend gave the computer to me,cause he couldn't seem to get it to work. so he said if i could soem how fix it i could keep it.  It is running Ubuntu 9.04.  It tried to reinstall it but it wont even boot off the disc just goes to a black screen ...please help

Your BIOS sounds like it is configured to boot from the hard drive, then the CD.
Change the boot order in your BIOS, or if supported use the alternative boot device menu, which can be accessed using Esc, F1, F2 or some other random F# key during boot.

---

### Post by siryuhan on 2009-06-26
This might be a shot in the dark, but try typing the following commands at the GRUB command line:

root(hd0, 1)
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/sda2 vga=791
boot

---

### Post by chris_castro on 2009-06-27
thank u so much it worked

---

