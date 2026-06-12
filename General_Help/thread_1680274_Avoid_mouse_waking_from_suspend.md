---
title: "Avoid mouse waking from suspend"
date: 2011-02-02
forum: General Help
---

### Post by pezlin on 2011-02-02
Hi all,

I am using my remote to wake the computer up from suspend. However I would like to disable so that if the mouse is moved it should not wake the computer. Is there a way to do so?

This is the result from lsusb:
Bus 002 Device 008: ID 0471:060c Philips 
Bus 002 Device 007: ID 413c:2010 Dell Computer Corp. 
Bus 002 Device 006: ID 413c:1003 Dell Computer Corp. 
Bus 002 Device 004: ID 046d:c703 Logitech, Inc. Elite Keyboard Y-RP20 + Mouse MX900 (Bluetooth)
Bus 002 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
Bus 001 Device 003: ID 1058:1101 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And this is the result from cat /proc/acpi/wakeup:
SMB0      S4     disabled  pci:0000:00:03.2
USB0      S4     enabled   pci:0000:00:04.0
USB2      S4     disabled  pci:0000:00:04.1
NMAC      S5     disabled  pci:0000:00:0a.0
PBB0      S4     disabled  pci:0000:00:09.0
HDAC      S4     disabled  pci:0000:00:08.0
XVR0      S4     disabled  
XVR1      S4     disabled  
P0P5      S4     disabled  
P0P6      S4     disabled  
P0P7      S4     disabled  
P0P8      S4     disabled  
P0P9      S4     disabled

Thanks for your help!

---

### Post by irv on 2011-02-03
I see no one came to answer your thread. May I suggest just unplugging the mouse or if you have a wireless, just turn it off.

---

### Post by ForrestUUID on 2011-02-03
I usually just turn the mouse upside-down, but doing a rmmod on the relevant module would probably do the trick. (And then modprobe it again after wakeup, of course.)

---

### Post by pezlin on 2011-02-03
> **ForrestUUID said:**
> I usually just turn the mouse upside-down, but doing a rmmod on the relevant module would probably do the trick. (And then modprobe it again after wakeup, of course.)

The problem is that I have a daughter that sometimes moves the mouse and there wakes the computer. Using rmmod and modprobe sounds interesting, can you please explain a bit more in detail how I implement it?

---

### Post by ForrestUUID on 2011-02-04
The general idea would be that you'd do a "sudo rmmod (module)" before standby and "sudo modprobe (module)" after restarting. What (module) would be would depend on the hardware; if it were a PS2 mouse it would be the psmouse module; the usb mouse (and keyboard) are handled by the usbhid (that's Human Interface Device on the end there) module.  What handles bluetooth mice I'm not sure, although a bit of googling suggests you can stop and start bluetooth itself with "sudo /etc/init.d/bluetooth stop" and "sudo /etc/init.d/bluetooth start", which would probably do just as well or better.

After another googlepause it seems there's some sort of laptop-mode configuration file, as mentioned here -- [http://ubuntuforums.org/showthread.php?t=1216839](http://ubuntuforums.org/showthread.php?t=1216839) -- that you could (conceivably) edit in order to to shut down and restart the bluetooth system automatically, but as it doesn't exist on my system, I can't really say much more about it.

EDIT: Now, if your remote control is itself bluetooth or otherwise handled by the same module that handles the mouse -- um, yes, you should probably just unplug the mouse.

---

