---
title: "WIndows Boot Manager/ GRUB"
date: 2010-07-21
forum: General Help
---

### Post by MistaMista on 2010-07-21
I am running Ubuntu 10.4 and I have dual OS's (Windows 7, Ubuntu). I want to know how to remove GRUB and just use the Windows Boot Menu, or does GRUB have to be installed to launch Ubuntu?

---

### Post by drs305 on 2010-07-21
I do not know about Windows bootloading but have seen some people state that EasyBCD might do what you want. Whether or not EasyBCD looks for Grub I don't know. A Google search will provide you more information on this app.

[http://en.wikipedia.org/wiki/EasyBCD]("http://en.wikipedia.org/wiki/EasyBCD")

---

### Post by wilee-nilee on 2010-07-21
Personally I would use grub, it is easier to manipulate and more accessible.

Here is the link to easybcd2 some have gotten this to work.
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

---

### Post by prodigy_ on 2010-07-21
You don't have to use Grub. Try [this HOWTO](http://blogs.technet.com/b/voy/archive/2006/10/13/how-to-use-windows-vista-s-boot-manager-to-boot-linux.aspx).

> Personally I would use grub, it is easier to manipulate and more accessible.
From my experience, Grub2 is very complicated, unreliable and often unpredictable.

---

### Post by mike555 on 2010-07-21
Ubuntu needs a boot manager of it's own (grub or lilo) but you could have install it to your Ubuntu partition then after making sure it works set it to a low timer number..  default is 10 sec. .... if your sure it works ok , you could set it to 0 ,then you don't even see it .. but of course if you need it to choose between os's then don't set it to 0 ...

---

### Post by wilee-nilee on 2010-07-21
> **prodigy_ said:**
> You don't have to use Grub. Try [this HOWTO](http://blogs.technet.com/b/voy/archive/2006/10/13/how-to-use-windows-vista-s-boot-manager-to-boot-linux.aspx).


From my experience, Grub2 is very complicated and often unpredictable.

That is a grub-legacy link from 2006, it doesn't apply to grub2 or ext4.

---

### Post by prodigy_ on 2010-07-21
> **wilee-nilee said:**
> That is a grub-legacy link from 2006
Yes, I know.

> it doesn't apply to grub2
So what? You can use grub legacy with 10.04.

> or ext4.
Grub legacy does work with ext4.

---

Anyway, the HOWTO I linked is just an example.

---

### Post by bobpress on 2010-07-21
EasyBCD will work.  After downloading EasyBCD (to your Windows partition), install Easy BCD and read over the instructions for creating a new start menu item.  You can then create a new start menu choice for Ubuntu which will use "NeoGrub"  a Windows/DOS based bootloader.

Restart Windows by choosing it through GRUB and then choose Ubuntu in the Windows start menu.  If Ubuntu starts, then you can remove GRUB and restore the Windows bootloader which can be done by EasyBCD under bootloader options.  I did this on my daughter's computer after installing Ubuntu because she uses Windows Vista most of the time.

---

