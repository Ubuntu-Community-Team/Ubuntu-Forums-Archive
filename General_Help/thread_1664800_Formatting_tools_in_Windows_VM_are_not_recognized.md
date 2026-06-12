---
title: "Formatting tools in Windows VM are not recognized"
date: 2011-01-11
forum: General Help
---

### Post by LetsMugSanta on 2011-01-11
Yeah so I am trying to make a multipass USB flash drive which basically turns say a bootable live iso into a flash drive, but many of them at once and accessing them using GRUB. The only issue I am having is I have to do this in Windows. So I am currently using my VM to do it and the Grub installer and petousb tool are not recognizing ANY drives at all on the system. I can use my usbs on the VM though. So my question is this, is there a way to make a multipass USB on straight ubuntu or is there a way to fix this issue in my VM.

---

### Post by uRock on 2011-01-11
Are you trying to make a bootable thumb drive?

If yes, then burn the iso to CD/DVD, then bot the LiveCD and go to System> Administration> Startup Disk Creator and use it to create the bootable Ubuntu thumb drive.

---

### Post by LetsMugSanta on 2011-01-11
It is not just for Ubuntu. Besides that method didn't work well for me in 10.10. I plan to have many tools such as trinity rescue kit, dsl, bt4, etc. And grub is used to choose between them on the USB thumb drive. Do a search of usb multipass on youtube and the first one should explain it in the first minute.

---

### Post by uRock on 2011-01-11
I would think it would be easier to just boot the installers and install them the same way as you would a multiboot. I previously have BT and ubuntu installed on a thumb drive that way and they worked fine. Using a VM to install sounds like the hard way.

---

