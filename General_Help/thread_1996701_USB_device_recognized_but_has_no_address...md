---
title: "USB device recognized but has no address..?"
date: 2012-06-04
forum: General Help
---

### Post by SeanMG on 2012-06-04
Good day folks,
  I'm trying to use a USRP1 with GNURadio if anyone knows what any of  that is. I am running Ubuntu on a Windows 7 machine via VMware player.  When I connect this USRP1 via USB 2.0 drive to Windows 7 it is  recognized as Ettus Research LLC USRP1... When I connect the device to  Ubuntu through VMware, it shows: usb device fffe:0002 on my removable  devices.

  When I run lsusb I receive the following:
  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub 
Bus 001 Device 004: ID fffe:0002    

When I run this program that comes with the USRP driver... uhd_find_devices I receive:
  -------------------------------------------------- 
-- UHD Device 0 
-------------------------------------------------- 
Device Address:     
type: usrp1     
name: 
serial: 00000000   

So when I run this program, it does recognize the fact that this  device is connected. However, the device has no address, no name, and  has a null serial. I need to know the device address so I can run more  programs in GNURadio. Does anyone know what the problem is here? 
  Thanks!

---

### Post by sanderj on 2012-06-04
If you live-boot Ubuntu on the bare metal, what does lsusb show then?

If it is different, it's a VMware thing
If it is the same, the problem is in the USB device or Ubuntu.

---

### Post by SeanMG on 2012-06-05
I was debating testing this... so I am going to test that tomorrow with my laptop switching to Ubuntu tonight. I believe it has something to do with VMware USB drivers...

---

### Post by SeanMG on 2012-06-06
Well, I tested it on a different machine that wasn't using VMWare to operate Ubuntu and have received the exact same result. Any suggestions?

---

### Post by matt_symes on 2012-06-06
Hi

Have a look at what dmesg is telling you.

Unplug the usb device.

Open a terminal and type

```
tail -f /var/log/dmesg
```

Plug the device in and wait 30 seconds.

Post back the output in the terminal.

Kind regards

---

### Post by SeanMG on 2012-06-06
Matt thanks for the reply,

######@ubuntu:/usr/local/bin$ tail -f /var/log/dmesg
[   22.132202] acpiphp: Slot [55] registered
[   22.132276] acpiphp: Slot [56] registered
[   22.132296] acpiphp: Slot [57] registered
[   22.132309] acpiphp: Slot [58] registered
[   22.132321] acpiphp: Slot [59] registered
[   22.132337] acpiphp: Slot [60] registered
[   22.132349] acpiphp: Slot [61] registered
[   22.132361] acpiphp: Slot [62] registered
[   22.132402] acpiphp: Slot [63] registered

Nothing changes after I plug in the USB and wait.

---

### Post by matt_symes on 2012-06-06
Hi

Just wanted to double check. 

1. You typed in the tail command
2. You the plugged in the USB device ?
3. You then post back the results of the tail ?

> **SeanMG said:**
> Matt thanks for the reply,

######@ubuntu:/usr/local/bin$ tail -f /var/log/dmesg
[   22.132202] acpiphp: Slot [55] registered
[   22.132276] acpiphp: Slot [56] registered
[   22.132296] acpiphp: Slot [57] registered
[   22.132309] acpiphp: Slot [58] registered
[   22.132321] acpiphp: Slot [59] registered
[   22.132337] acpiphp: Slot [60] registered
[   22.132349] acpiphp: Slot [61] registered
[   22.132361] acpiphp: Slot [62] registered
[   22.132402] acpiphp: Slot [63] registered
[   22.135796] init: alsa-restore main process (859) terminated with status 19

The only reason i ask is because there is no USB device registered at all in the above log.

Kind regards

---

### Post by SeanMG on 2012-06-06
Yes sir, I did exactly as you said and I received that output. I saw the error message and thought that was odd, because I haven't seen it before, restarted my computer and now I receive just: 

######@ubuntu:/$ tail -f /var/log/dmesg
[   20.125011] acpiphp: Slot [54] registered
[   20.125308] acpiphp: Slot [55] registered
[   20.125628] acpiphp: Slot [56] registered
[   20.125964] acpiphp: Slot [57] registered
[   20.126262] acpiphp: Slot [58] registered
[   20.126560] acpiphp: Slot [59] registered
[   20.126857] acpiphp: Slot [60] registered
[   20.127153] acpiphp: Slot [61] registered
[   20.127452] acpiphp: Slot [62] registered
[   20.127470] acpiphp: Slot [63] registered

If I run dmesg this is at the end of dmesg and is about USB devices:

[   86.737433] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[  152.837793] usb 1-1: USB disconnect, device number 2
[  160.392211] usb 1-1: new high-speed USB device number 3 using ehci_hcd
[  174.998692] usb 1-1: USB disconnect, device number 3
[  207.559314] usb 1-1: new high-speed USB device number 4 using ehci_hcd
[  427.309201] usb 1-1: USB disconnect, device number 4
[  436.283856] usb 1-1: new high-speed USB device number 5 using ehci_hcd
[  730.950820] usb 1-1: USB disconnect, device number 5
[  735.274217] usb 1-1: new high-speed USB device number 6 using ehci_hcd
[  745.104425] usb 1-1: USB disconnect, device number 6
[  754.524724] usb 1-1: new high-speed USB device number 7 using ehci_hcd
[ 1014.778357] usb 1-1: USB disconnect, device number 7
[ 1034.438139] usb 1-1: new high-speed USB device number 8 using ehci_hcd
[ 1040.626997] usb 1-1: USB disconnect, device number 8
[ 1047.892753] usb 1-1: new high-speed USB device number 9 using ehci_hcd

---

### Post by SeanMG on 2012-06-06
Well.... this is strange, because I shut down and restarted the computer yet again and now it shows: 

######@ubuntu:~$ tail -f /var/log/dmesg
[   29.162688] acpiphp: Slot [55] registered
[   29.162890] acpiphp: Slot [56] registered
[   29.163090] acpiphp: Slot [57] registered
[   29.163589] acpiphp: Slot [58] registered
[   29.163802] acpiphp: Slot [59] registered
[   29.164152] acpiphp: Slot [60] registered
[   29.164174] acpiphp: Slot [61] registered
[   29.164199] acpiphp: Slot [62] registered
[   29.164220] acpiphp: Slot [63] registered
[   29.187733] init: udev-fallback-graphics main process (964) terminated with status 1

:confused:

---

### Post by matt_symes on 2012-06-06
Hi

That looks a bit better and is more of what you expect to see and not the ACPI hotplug driver.

For some reason it seems to keep disconnecting though.

Let's try to use the old usb format.

Unplug the device.

Open a terminal and type

```
echo Y | sudo tee /sys/module/usbcore/parameters/old_scheme_first
```

Enter your password. It will not be echoed not the screen.

Plug the device in. How does that get on ?

Kind regards

---

