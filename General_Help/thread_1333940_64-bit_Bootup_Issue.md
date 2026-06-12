---
title: "64-bit Bootup Issue"
date: 2009-11-21
forum: General Help
---

### Post by KiraLexi on 2009-11-21
When booting on my IA64 system, the computer doesn't recognize that there's a disc in the drive and just boots into Windows. I'm not sure how to force it to use the disc in the boot order first. Any ideas?

---

### Post by jolx on 2009-11-21
"Your computer's BIOS must be set to boot from CD first; otherwise, Windows will just load up again. To get into the BIOS settings, you usually have to press one of these keys during boot-up: Escape, F1, F2, F12, or Delete. Usually your computer will tell you which key to use."
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by KiraLexi on 2009-11-21
Since this is an IA64 system, its using EFI instead of BIOS. There's some EFI strangeness going on - I can't connect the keyboard until after I'm already booting an OS. Is there a way to modify the EFI menu from within Windows or Fedora so that I can put the CD/DVD boot as the default?

---

### Post by jolx on 2009-11-21
does [this]("https://help.ubuntu.com/9.10/installation-guide/ia64/ch05s01.html") help at all?
also, [https://launchpad.net/efibootmgr]("https://launchpad.net/efibootmgr")

---

### Post by KiraLexi on 2009-11-22
YES, thanks a lot. EFI Boot Manager was indeed what I was looking for.

---

