---
title: "Cant add one particular usb device to virtualbox"
date: 2011-02-13
forum: General Help
---

### Post by eNRGy on 2011-02-13
Hi all,

I have a WinTV-Nova-S-USB2 which I'd like to use with VirtualBox (WindowsXP guest) because it isn't supported by Ubuntu. (It's a DVB-S tv tuner)

It shows up in the Devices menu in VirtualBox but when I click on it, I get this error message popup:
```

Failed to attach the USB device **HCW WinTV Model 46xxx [0001] ** to the virtual machine

Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).

Details:
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}

```
Naturally there's no sign of the device in Windows as it isn't even attached to the VM, so not a Windows issue.

Dmesg when I unplug and plug it back in shows this:
```

[ 2957.973257] usb 1-3: USB disconnect, address 4
[ 2963.081275] usb 1-3: new high speed USB device using ehci_hcd and address 5

```

I have a well established VBox/WindowsXP which I use with several USB bits and bobs and for the occasional Windows only tasks. Other direct USB stuff works just fine, syncing phones, my Logitech Harmony TV remote and such like. This is the first USB device it has fallen over on.

Based on my googling research efforts, I suspect that Ubuntu is picking up the USB and "using" it in some way, preventing it from being handed over exclusively to the guest. If that was the case, how could I diagnose and release it? Why would it affect this specific device and not others?

I'm stuck with this USB hardware as it's for a laptop and this was the only USB satellite receiver I could actually find to buy..! (It's a long story why I want satellite tv on a laptop. :p )

Host: Ubuntu 10.10 i686
Guest: Windows XP
VirtualBox: v3.something to start with
Now upgraded to v4.02 while trying to solve this. (plus the new usb extension, required for v4)

Any thoughts gratefully received as I'm tearing my hair out over this.

TIA!

---

### Post by sieve on 2011-04-29
Same problem here.

eta - solved.  Played around with the settings in the vbox control panel.  It automatically recognized the USB device and populated the necessary fields.

---

