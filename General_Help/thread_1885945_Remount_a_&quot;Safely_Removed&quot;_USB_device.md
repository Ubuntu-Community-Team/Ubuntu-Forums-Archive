---
title: "Remount a &quot;Safely Removed&quot; USB device"
date: 2011-11-24
forum: General Help
---

### Post by Daniel15 on 2011-11-24
My computer has a SD card reader at the front of it, in a 3.5 inch drive bay. Internally it's connected via USB to a USB header on the motherboard. lsusb shows it as:
> 
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer


It works very well - When I insert an SD card from my camera, Ubuntu mounts it, asks what I want to do with it (like open Shotwell or the folder) and all works well. However, if I choose "Safely Remove", the USB device disappears from the system (not even in a "lsusb" listing any more) and I can't seem to find a way to bring it back. I guess this is expected, but since it's internally connected using USB and the cable is inside my computer, I can't unplug it and plug it back in to bring it back.

Is there a command I could run to bring it back after accidentally using "Safely remove"? I can reboot, but that's a lot of effort :P

---

### Post by jjex22 on 2011-11-24
Unfortunately this is a known bug that's been around for ages. From what I understand the problem lies with how your media reader identifies itself to ubuntu, and the devs have done all they can to resolve it - meaning it's currently unfixable.

To explain, the options you have for media are as follows:

Unmount - designed for internal partitions and drives.
Eject - designed for disk drives - unmounts and sends an eject signal to the device.
Safely Remove Device - designed for external hard drives; unmounts and cuts power to the device.

As you can see, there isn't one specifically designed for media readers, because all the options are covered. The problem is your hardware isn't telling Ubuntu it isn't hot pluggable, so Ubuntu still lets you use 'Safely Remove Device'. In response to this issue Ubuntu has changed the default removal option for usb devices in nautilus to 'eject' - which also covers external cd drive issues.

The problem is that Safely Remove Device looks so similar to the Windows option for removing USB devices that people still choose it over the default - Renaming has been suggested, but in the meantime I'm afraid it's just a case of don't use that option; Because Safely Remove cuts the power, there is no way to remount it until the system restarts.

---

### Post by dandnsmith on 2011-11-24
Addendum to jjex22 posting:

Exactly the same happens under Windows, as my wife can attest.
My solution for either OS is to use the eject command/option - after all all you want to achieve is closing the filesystem, not remove the device (which is what the *safely remove* will achieve).

I don't have a way to get it back, apart from rebooting.

---

### Post by Daniel15 on 2011-11-24
> The problem is your hardware isn't telling Ubuntu it isn't hot pluggable
Makes sense; technically it's a USB device so it probably doesn't even know it's not hot pluggable.

> Because Safely Remove cuts the power, there is no way to remount it until the system restarts.
Okay, thanks, I'll keep this in mind :)

---

