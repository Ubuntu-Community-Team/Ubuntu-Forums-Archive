---
title: "Boot menu"
date: 2010-12-12
forum: General Help
---

### Post by ppnl on 2010-12-12
I have an alienware computer running windows 7 professional. I recently put in a new hard drive, unplugged the windows hard drive and installed ubuntu 10.10(32 bit). I installed ubuntu with the windows disk disconnected because in the past I have had trouble with accidental trashing of the windows MBR.

Now both the windows and ubuntu installs appear to be working well. The only problem is that in order to switch from one operating system to the other I have to go into the system bios and switch the boot order of the drives.

Is there any simple way to choose which disk to boot from a menu on boot up without going through bios? Preferably without endangering the windows MBR. My last experiment with ubuntu was cut short when it trashed my windows install for reasons I did not understand. I didn't lose anything but it did annoy me.

Also I first attempted to install ubuntu(64bit) but it crashed out with the suggestion that I had a corrupted ubuntu cd. I burned the disk twice and checked it but could not get it to install. This is not an important problem now but I would like to eventually understand what is going on.

---

### Post by Quackers on 2010-12-12
You could try booting from the Ubuntu hard drive and then open a terminal and run ```
sudo update-grub
```
then watch to see if the Windows installation is picked up as grub.cfg is configured. If it is you can reboot and try to boot Windows from the grub menu.

---

### Post by ppnl on 2010-12-12
> **Quackers said:**
> You could try booting from the Ubuntu hard drive and then open a terminal and run ```
sudo update-grub
```
then watch to see if the Windows installation is picked up as grub.cfg is configured. If it is you can reboot and try to boot Windows from the grub menu.

Dude, that was awesome. Thanks a bunch.

---

