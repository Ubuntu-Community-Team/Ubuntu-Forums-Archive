---
title: "can't boot into windows"
date: 2011-01-13
forum: General Help
---

### Post by ashnova22 on 2011-01-13
I am posting from my phone, its tedious to say the least so I will have to keep short.

I installed ubuntu alongside w7 yesterday. after updating ubuntu I could no longer boot into ubuntu. long story short, deleted ubuntu partition in Windows, now I get;

error unknown file system 
grub rescue:

any ideas how I can start using my machine again ? 

appreciated, 

ashley.

---

### Post by TeoBigusGeekus on 2011-01-13
When you installed ubuntu, the grub (ubuntu's bootloader) was installed in your system. This little app helps you choose which os you want to boot from when you start your pc. After deleting ubuntu, grub is orphan and can't find its default os (ubuntu). 
So basically, you want to fix your master boot record deleting grub.
A quick googling brought up [this]("http://www.lukeaddison.com/removing-linux-grub-restoring-windows-7-boot-gui/").
Feel free to repeat the search if you want to...

---

### Post by Mark Phelps on 2011-01-13
And ... when you get back into Win7, if you plan on messing around with dual boot or Linux distos again, do yourself a favor, and use the Backup feature to create and burn a Win7 Repair CD.

That way, if the MBR or boot loader needs repair in the future, you will already have a CD in hand to do that.

---

