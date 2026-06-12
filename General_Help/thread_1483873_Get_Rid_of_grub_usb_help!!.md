---
title: "Get Rid of grub usb help!?!"
date: 2010-05-15
forum: General Help
---

### Post by zefeldo on 2010-05-15
I have installed the ubuntu 10.04 disk onto a usb thinking I could just boot it up anywere and would not have to use the universal installer thing, and i somehow installed grub onto my windows 7 laptop. i have no disk of any kind to re install or repair windows 7, it has already been repaired from staples and i have no system recovery so im pretty much screwed. i cannot take it back because i have no money. Why the hell did it install grub onto my computer. now i have to have the usb in to boot anything. its gay and i would not want this. how do i remove it without a disk of any kind other than ubuntu. or right from the ubuntu i installed onto the usb?

---

### Post by mcduck on 2010-05-15
Plug in the USB drive, boot into Windows, and create the repair CD there. (You should be able to do that in Win7 by executing "recdisc" in the run dialog)

Reboot with your brand new Windows repair CD and fix the MBR.

..and next time you try too install Ubuntu to a removable drive, note the "advanced"-button in the last dialog of the installer. Click that and you'll be able to choose where to install the Grub bootloader....

(It installed the Grub  since it needs it. Every operating system needs a bootloader to load the OS kernel from disk to RAM and to start it, Windows uses ntldr or winload.exe, and Ubuntu uses Grub.)

---

### Post by zefeldo on 2010-05-15
im guessing by what you said you still dont know what i mean.. i cannot create any type of recovery/startup disk because that partition has been destroyed some time ago when trying to put mac on my pc. yea dumb choice but when you say that i am wondering if any installation disk will work for that. as in if my windows 7 was home edition and the disk was premium or whatever edition it would still work.. anyway thanks for trying to help me.

---

### Post by zefeldo on 2010-05-15
oh and another thing is. if i tried to install ubuntu or mint or something onto my computer will it have no need for the usb to boot and i could have linux and windows on the same computer so then i would not have to go through the trouble to get grub out. The only thing is i dont want to mess up my computer more than i already have.

---

### Post by chayes19 on 2010-05-15
> **zefeldo said:**
> oh and another thing is. if i tried to install ubuntu or mint or something onto my computer will it have no need for the usb to boot and i could have linux and windows on the same computer so then i would not have to go through the trouble to get grub out. The only thing is i dont want to mess up my computer more than i already have.

Paragon Partition Manager should get rid of the grub boot loader which is available from [http://www.paragon-software.com/home/pm-personal/](http://www.paragon-software.com/home/pm-personal/)

---

### Post by mcduck on 2010-05-15
> **zefeldo said:**
> oh and another thing is. if i tried to install ubuntu or mint or something onto my computer will it have no need for the usb to boot and i could have linux and windows on the same computer so then i would not have to go through the trouble to get grub out. The only thing is i dont want to mess up my computer more than i already have.

If you now install Ubuntu (or any other linux distribution) to the computer itself (not into USB drive) the installer will make a new install of Grub into your hard drive, giving you a menu to choose between Windows and Ubuntu (or whatever Linux distro you used). So yes, that would give you back a system that works without needing the USB drive.

What comes to using a different version of the Windows disc than what you have installed might work, since you don't actually need to install Windows, just access the recovery options from the disc. But as far as I know the recdisc command in Windows shouldn't require any recovery partition made by the computers manufacturer or anything like that, it simply requires a working Windows install. The disk created will not be able to restore all the programs and drivers that came with the machine, it just for repairing Windows itself.

---

