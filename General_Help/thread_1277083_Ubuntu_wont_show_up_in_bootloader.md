---
title: "Ubuntu wont show up in bootloader"
date: 2009-09-27
forum: General Help
---

### Post by xxhopingtearsxx on 2009-09-27
I'm using the Windows Boot Manager, and I installed Ubuntu with Wubi and it wont show up when I boot my PC. I can't boot from CD because when I try, I only get green lines as if I'm playing a broken cartridge on an old Nintendo. It's done that on pretty much most of my successful installations, so I don't think that's a huge problem.

I tried adding Ubuntu on EasyBCD but it keeps me on a msdos-like screen that says "Grub".. which is another issue, but I made two threads here and no one is responding to me (thanks for nothing :[) so I'm just going to let that go.

Please help.

---

### Post by Darkwing-Duck on 2009-09-28
If you cannot boot from CD then try to burn the ISO to a UBS thumbdrive. From windows you can do this from this program. [https://launchpad.net/win32-image-writer/+download](https://launchpad.net/win32-image-writer/+download)

Okay, once you're done with that open BIOS and set your boot menu to boot from USB device. When that is done boot from the USB and into the LiveCD. 

Once there you can reset GRUB and use that to dualboot your system. Use this guide to help you with that. 

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this helps you out.

---

### Post by xxhopingtearsxx on 2009-09-28
Wouldn't that install Grub though?

I want to use something familiar like Windows Boot Manager.. Would I be able to keep that somehow? I have Ubuntu on my PC.. There's just no way to get to it.

---

### Post by xxhopingtearsxx on 2009-09-28
Bump.. somebody please give me an answer.

---

### Post by xxhopingtearsxx on 2009-09-28
Bump.. Come on! I really want to get an answer. All I asked was

"Wouldn't that install Grub though?"

---

### Post by hxleet on 2009-09-28
> xxhopingtearsxx 	 		**Re: Ubuntu wont show up in bootloader**
 		Bump.. Come on! I really want to get an answer. All I asked was

"Wouldn't that install Grub though?"

Correct me if im wrong but dont you need GRUB installed to get into ubuntu.  If you install GRUB you will see all your OS choices.  I mean its not hard you got a 10 sec delay(at least i do) to choose which OS you want. Windows is usally at the bottom and your linux distros will be at the top.  Try using the iso cd disk and run it live and go to System>Admin>Gparted and format your ubuntu partition and reinstall WITH GRUB and you will be able to get into ubuntu.  I dont think you can keep windows boot manager.  GRUB is straight forward just use your arrow keys to go up and down and select which OS you want. Or try DD's solution before posting again about getting no help.

---

