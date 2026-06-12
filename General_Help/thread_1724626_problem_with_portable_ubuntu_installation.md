---
title: "problem with portable ubuntu installation"
date: 2011-04-08
forum: General Help
---

### Post by rpare89 on 2011-04-08
I tried to install ubuntu 10.04 to a 16 gig thumb drive and the installation went perfectly. However, when I removed the thumb drive and tried to boot the computer back into windows I saw that the installer had installed GRUB on to the hard drive of the computer. Windows runs fine, but it wont start with out the thumb drive that has the ubuntu install on it, this is very bad for me. Is there a way I can remove GRUB with out messing up windows on the computer? i dont have a windows 7 boot disk so this operation would need to be done either in windows (already booted) or ubuntu.

---

### Post by earthpigg on 2011-04-08
hi,

you went wrong at one of the final stages of installing ubuntu onto that thumb drive. there was an 'advanced options' button you should have clicked to specify were to install grub onto.

here is Microsoft's documentation to fix this problem:

[http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)

> To use system recovery options, you'll need a Windows installation disc or access to the recovery options provided by your computer manufacturer. **If you don't have either of those choices, you can create a system repair disc to access system recovery options.**

the relevant option you want to look for when using that is something like 'restore MBR' or 'reinstall windows bootloader' or something along those lines.

---

### Post by rpare89 on 2011-04-08
that'll do pig, that'll do.
but thank you so much for the help, i was because i know new windows computers stopped shipping with recovery discs and feared it would be difficult to make one from windows. 

so using the disc i should get windows to boot regularly. would i have to reinstall ubuntu on the usb with grub, or should it boot from the usb drive with out it if i make it the primary boot device?

---

### Post by C.S.Cameron on 2011-04-08
The USB will still boot ok and you will also have an option to boot Windows with the USB's grub.

---

