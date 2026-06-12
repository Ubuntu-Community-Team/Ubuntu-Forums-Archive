---
title: "Hotplug subsystem hang!!"
date: 2006-03-21
forum: General Help
---

### Post by Sublime10 on 2006-03-21
I recently installed Breezy Badger on a second hard drive on my computer. I have it set to dual boot with windows. However, when I boot up into breezy everything loads OK until the hotplug subsystem. I've been searching through the forums for about 3 days now, and nothing I've found has helped me. I have an HP computer, not sure of all the specs though. So far I've tried turning off the onboard sound and LAN in the Bios, unplugging all USB devices during the boot and even unplugging everything except the monitor to no avail. I tried to install Breezy with different commands, like turning off acpi during install, still didnt work. 

Please help... Im getting really frustrated

---

### Post by dcstar on 2006-03-22
[QUOTE=Sublime10]I recently installed Breezy Badger on a second hard drive on my computer. I have it set to dual boot with windows. However, when I boot up into breezy everything loads OK until the hotplug subsystem. I've been searching through the forums for about 3 days now, and nothing I've found has helped me. I have an HP computer, not sure of all the specs though. So far I've tried turning off the onboard sound and LAN in the Bios, unplugging all USB devices during the boot and even unplugging everything except the monitor to no avail. I tried to install Breezy with different commands, like turning off acpi during install, still didnt work. 

Please help... Im getting really frustrated[/QUOTE]
Try booting into Recover mode - or with the install CD - and try any mount your drive and edit the following files (you may need to do a forum search for exact details on how to do this):

/etc/default/bootlogd
```
BOOTLOGD_ENABLE=Yes
```
/etc/default/rcS
```
VERBOSE=yes
```
The first should enable you to see the boot messages in a log file, the second should increase the level of detail so you may see exactly what part of the hotplug subsystem is freezing your system.

---

### Post by Sublime10 on 2006-03-26
[QUOTE=dcstar]Try booting into Recover mode - or with the install CD - and try any mount your drive and edit the following files (you may need to do a forum search for exact details on how to do this):

/etc/default/bootlogd
```
BOOTLOGD_ENABLE=Yes
```
/etc/default/rcS
```
VERBOSE=yes
```
The first should enable you to see the boot messages in a log file, the second should increase the level of detail so you may see exactly what part of the hotplug subsystem is freezing your system.[/QUOTE]



I used the install cd to boot into rescue mode and I mounted my hard drive. When I put the commands in though, it said:

```

Sc-3.00#  etc/default/bootlogd: Permission Denied
```

[COLOR="Red"]EDIT:[/COLOR]
Nevermind, i figured that out.

---

### Post by Sublime10 on 2006-03-27
[FONT="Courier New"]I figured out what has been making it hang... When I boot up it stops after the Hotplug Subsystem at PCI, which im guessing is my video card? I have an NVIDIA GeForce4 MX 4000.
[/FONT]

---

### Post by DOtSlaSHuCantCME on 2006-03-27
[QUOTE=Sublime10][FONT="Courier New"]I figured out what has been making it hang... When I boot up it stops after the Hotplug Subsystem at PCI, which im guessing is my video card? I have an NVIDIA GeForce4 MX 4000.
[/FONT][/QUOTE]


Hi

this is what got me passed the hotplug hang...you have to go Bios and go to advanced ,there is a option to place your primary vid card as pci or onboard,onboard video should be placed as onboard not pci.thats what got me
past the hang....i too use a NVIDIA Geforce mx.For whatever reason my onbaord was set to pci instead of onboard, when i changed my (after weeks of frustation)onboard to pci ubuntu just skipped hotplug and kept on booting.

---

### Post by Sublime10 on 2006-03-27
Thanks, I'm gonna try that now.

---

### Post by Sublime10 on 2006-03-28
[QUOTE=DOtSlaSHuCantCME]Hi

this is what got me passed the hotplug hang...you have to go Bios and go to advanced ,there is a option to place your primary vid card as pci or onboard,onboard video should be placed as onboard not pci.thats what got me
past the hang....i too use a NVIDIA Geforce mx.For whatever reason my onbaord was set to pci instead of onboard, when i changed my (after weeks of frustation)onboard to pci ubuntu just skipped hotplug and kept on booting.[/QUOTE]
 
 My Computer was already set to PCI graphics so i changed it to onboard. I had to move my monitor cable from my NVIDIA slot to my onboard slot and now I'm guessing this only runs my onboard graphics. It might be possible for me to install linux drivers for the NVIDIA card to solve this, but then I'm afraid that the card won't work when I boot windows. **Does anyone know of some way that I can fix the bootup hang when I use my NVIDIA card?** I would like to be able to leave it plugged in all the time instead of having to move my cable every time I want to boot into a different system... Help would be greatly appreciated.

---

