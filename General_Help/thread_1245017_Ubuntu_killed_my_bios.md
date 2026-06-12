---
title: "Ubuntu killed my bios?"
date: 2009-08-20
forum: General Help
---

### Post by tarodin on 2009-08-20
Hello,

i'm a spanish user and the spanish forum is not working, so i will try to explain with my best english.

Thanks in advance for your comprehension.

First of all, i'm a windows xp user because i use traktor scratch pro and at moment there is no compatibility with this program on linux.

I installed ubuntu and all it's ok with that, but, when i start windows XP a blue screen flashes and reboot my computer.
I reinstalled windows and the same error happend, blue screen with a mention of ACPI.

Yesterday, i don't know how, windows started and i could use it.

So, this morning, the same error. I can't start windows. I tried to switch off ACPI from the bios, but it wont help. I switched it on again.
I was running windows with this computer for three years.
I installed ubuntu and i can't use it.

Any idea to fix it?

Windows safe mode works sometimes but i can't do anything from there.

Please, help me...

---

### Post by dreamingdarkness on 2009-08-20
If the error is coming up as an ACPI problem, you may need to fix or re-write the Master Boot Record. 
You can use the Super Grub Disk to repair this, the instructions and downloads are at:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
I had to do this once, when I first installed Ubuntu on my laptop, but after that (and getting Grub how I wanted it) it has been easier. Hope this helps! If not, someone with more experience may post about how to do it step-by-step.

---

### Post by tarodin on 2009-08-20
i burned a boot cd with supergrub but it only shows me the linux boot... not windows...

---

### Post by tarodin on 2009-08-20
i just installed the KgrubEditor... how can i activate the acpi or what i should do there??? :'(

---

### Post by dreamingdarkness on 2009-08-20
Ok, so you have a Super Grub Disk?
Well, there are a few options to go with from here.
Worst case scenario, if you absolutely must boot Windows, you can use a Windows boot disk, get a recovery console, command prompt, and then fdisk /mbr  - that should re-write your Windows Master Boot Record into the boot record, wiping out your current Grub install and letting you at least get some operating system up.

However, to fix it so you can boot both Linux and Windows from the same PC is trickier, though I found it was worth some time and I no longer really boot Windows except when I need certain programs.
The best instructions start out from:
[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)
It gives both visual and step-by-step instructions though in English, sorry I can't manage to put them en espanol for you but I speak just enough Spanish to start a bar-fight :lolflag:

If you reinstall Windows but want stuff from your Linux partition, you may want to give this a shot:
[http://www.supergrubdisk.org/w/index.php5?title=AutoSuperGrubDisk](http://www.supergrubdisk.org/w/index.php5?title=AutoSuperGrubDisk)

And as a last note, this is the best website I found for dual-booting though I don't know if anything has changed with 9.04 since I upgraded from 8.10 Ubuntu:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Tons of resources and really detailed info, but the colors are sort of rough :) 
All credit goes to the people I linked to, not me

---

### Post by tarodin on 2009-08-20
hehe!!! i can't start with the windows installation cd... blue screen with bad_pool_header message or something like that.

I start windows on safe mode but i dont have fdisk...

i cant do anything... well, i can use ubuntu, but this is not my initial purpose...

any idea for do fdisk /mbr from linux?

thanks

---

