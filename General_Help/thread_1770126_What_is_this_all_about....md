---
title: "What is this all about...???"
date: 2011-05-28
forum: General Help
---

### Post by robertcoulson on 2011-05-28
When I log on to some distros, I get this error (see attachment)...Don't know what it means..Does anyone know...?
Robert

---

### Post by linuxinstalledfromhdd on 2011-05-28
Have you flash updated your BIOS since you bought the computer?

---

### Post by robertcoulson on 2011-05-28
No..I have not..Don't know how to go about doing that...
Robert

---

### Post by linuxinstalledfromhdd on 2011-05-28
Have you contacted the manufacture of the computer yet asking to find out?

---

### Post by Rubi1200 on 2011-05-28
The message is related to VirtualBox, which you are running. See here for more details especially the comment by Frank Mehnert at the end of the first page.
[http://forums.virtualbox.org/viewtopic.php?f=1&t=29116](http://forums.virtualbox.org/viewtopic.php?f=1&t=29116)

---

### Post by robertcoulson on 2011-05-28
Was just doing that right now...Funny, it bypasses the error and works great, with no problems....
Robert

---

### Post by linuxinstalledfromhdd on 2011-05-28
If you have the unit still under warranty and you intend on keeping it for the life of the unit, it would probably be a good idea to update the BIOS if the manufacture has updated something to do with that error specifically.

---

### Post by robertcoulson on 2011-05-28
Rubi1200..You are correct sir...It only happens in virtualbox and not when I log in on Ubuntu 10.10...Guess, I don't have to worry...???
Robert

---

### Post by Rubi1200 on 2011-05-29
It's a VirtualBox issue not a BIOS issue. If you search on their forums you may find more information and even some workarounds.

---

### Post by yetiman64 on 2011-05-29
> **Rubi1200 said:**
> It's a VirtualBox issue not a BIOS issue. If you search on their forums you may find more information and even some workarounds.

Here is one such "fix", haven't tried it myself yet but need to, it is reported to work,

[http://finster.co.uk/2010/11/16/virtualbox-piix4_smbus-error/](http://finster.co.uk/2010/11/16/virtualbox-piix4_smbus-error/)

Although this article is for version 3.2 it basically is just blacklisting an Ubuntu module and updating initramfs in the guest OS.

Cheers, yetiman64

---

### Post by robertcoulson on 2011-05-29
Thank you Rubi1200 and Yetiman64 for your help and links...Much appreciated....Will try to rectify asap...One of the links referred to it as an annoyance at best and did not affect the OS's performance.
Robert

---

