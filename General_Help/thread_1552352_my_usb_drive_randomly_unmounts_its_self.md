---
title: "my usb drive randomly unmounts its self"
date: 2010-08-13
forum: General Help
---

### Post by rexxxlo on 2010-08-13
im running lubuntu 10.04 on my asus eee701 and have a 2.5" hp simple save usb hdd

i upgraded the usb cable to a dual plug on the computer end to make sure it has enough juice to run it

i have it formatted ext4 and there is a small partition for the hp software but it it empty and has never caused me any problems before i can have it mounted or unmounted it makes no difference.

i am running the laptop on mains power with all the power saving options turned off such as spin down drives or black screen when idle.

randomly it unmounts itsself and turns off 
> lsusb
shows its still there but i have to un plug and replug it in to make it mount again.

what do i do ?

---

### Post by cavalier911 on 2010-08-13
Even a 2.5" drive without it's own powersupply is a bad idea.The drive may be warning you it's failing,last thing you want to happen is for the drive to fry the usb port on your netbook.If the drive is electrically turning off the netbook's usb power can no longer reliably supply adequate current/voltage to keep it running.I would plug the usb drive into a powered usb hub which has it's own power adapter so the drive isn't sucking any power from the netbooks usb power bus. Just like with usbflash drives once the drive is registered as a usb device it is normal that it would still be registered (lsusb)until you manually unplug the drive's usb connector.Doesn't matter if it's mounted or the drive has stopped running.

---

### Post by earthpigg on 2010-08-13
hi,

do you know what lubuntu uses for power management?

in ubuntu, we have gnome-power-preferences that is found in system -> preferences -> power management. 

there is a check box there titled "spin down hard disks when possible".

find the equivalent in lubuntu, and give that a try.

---

