---
title: "Add OS X to GRUB?"
date: 2009-06-29
forum: General Help
---

### Post by PooingCavy on 2009-06-29
Hey guys, I am in the process of installing OS X, but I can't find out how to add it to the GRUB list... I have menu.lst open right now...

I also have Windows 7 on here, and it looks like this:

title Windows 7
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

I'm guessing for adding OS X, I copypasta that block, and change 'title Windows 7' to 'title Mac OS X Leopard", and "rootnoverify (hd0,0)" to "rootnoverify (hdX,X)"

How do I determine the number? I keep going into properties and stuff, but my googling skills are failing me today and I don't know how to look up the terminal command for it... Help would be appreciated.

---

### Post by NikolaiKalashnikov on 2009-06-29
Use GRUB Editor,it can be found on the Package Manager,that's what I used for my Ubuntu/XP/Debian/Gentoo/Vista/OSX/Slax  setup.
Nikolai.

---

### Post by PooingCavy on 2009-06-29
Ah, nevermind, I found out myself through logic...

[http://www.linuxmigration.com/quickref/kernel/grub.html](http://www.linuxmigration.com/quickref/kernel/grub.html)

Studied that, and I found that /dev/sda(n) translates to (hd0,(n-1)), and I found out OS X was /dev/sda2, so it was (hd0,1)

---

