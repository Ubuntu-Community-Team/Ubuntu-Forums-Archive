---
title: "Where to edit grub settings"
date: 2010-01-21
forum: General Help
---

### Post by pcal on 2010-01-21
Hi folks,

I'm using a karmic netbook remix on usb drive to dual boot a fujitsu m2010 (works great right out of the box!) I've
installed karmic on other pc's, but on the netbook I want to have ubuntu as a plug in option rather than installing it to hdd, and I would like to edit the grub settings on the usb drive so it boots directly rather than going through the "what language" and "which boot options" screens first.

I went to edit the file in the /boot/grub directory but it wasn't there... Where do I look to find this, and is there anything special I will need to know to edit it?

Basically, all I want it to do is load Ubuntu automatically if the usb is plugged in, and load the standard os if it isn't - I don't need or want the traditional dual boot menus, and the bios takes care of choosing which drive, so I figure it should be simple if I can find the boot options settings for the netbook remix somewhere...

Thanks in anticipation.

pcal

---

### Post by pcal on 2010-01-28
Does the 9.10 NBR even use grub? Please, what is the boot manager used on this re-mix? Grub is all I have any experience of, but the grub config file isn't there so I presume it's not being used.

Have tried searching for the info, but nothing is coming up...

Thanks

---

### Post by sisco311 on 2010-01-28
GRUB 2 is the default boot loader and manager for Ubuntu 9.10 (Karmic Koala).

[uhelp]community/Grub2[/uhelp]
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]

---

### Post by MerlinW on 2010-01-28
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by pcal on 2010-01-29
:D Thanks guys...

I see I have some reading to do...

Cheers,

Pcal

---

