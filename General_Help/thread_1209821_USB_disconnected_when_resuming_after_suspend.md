---
title: "USB disconnected when resuming after suspend"
date: 2009-07-10
forum: General Help
---

### Post by b166er on 2009-07-10
Hi all
Iv'e experienced a little inconvenience since I installed Jaunty 9.04.
Every time after I "un-suspend" (wake) my computer, I have to unplug and replug my usb devices in order to get them to work again. 
Or actually unplug-replug my usb-hub will do.

I think that this might have to do with my USB setup.
I have two keyboards (one wireless), one mouse and one "Wacom intuos3" connected to my Usb-hub. The Usb-hub is then connected to a Usb-repeater (extender) which is then connected to the computer. 

I need all these devices because my desk is located five meters from my computer.

My guess is that there is a "Usb-suspend"-command that is sent to all devices whenever a computer suspends. That seams to work ok.

But the corresponding "Usb-wake-up"-command gets lost somewhere in my usb-setup when resuming from suspend.

Assuming that all this would be true, I can only see two ways of solving this problem:
Either making Ubuntu stop sending the "Usb-suspend"-command when suspending. 
Or making the "Usb-wake-up"-command work.
I'm happy either way.

So does anyone know how to modify the suspend-sequence?;)



P.s 
All this works fine in XP,Vista and OSX. 
(Yes, I Quad-boot):p

---

### Post by ddrichardson on 2009-07-10
If you know which module is not waking then you can suspend it/wake it by adding it to /etc/pm/config.d/modules:```

SUSPEND_MODULES="ath5k"
```

I'd try usbcore first.

---

### Post by b166er on 2009-07-10
Sorry
Whilst I know some about Linux, I've never had problems with USB. So I don't know much about usb stuff.

So how can I get module names?

And looking at that command, Wouldn't that just tell it to suspend the device? I want it to not suspend. Or alternatively make sure the device does wake up.

Does "ath5k" mean the usbcore?.
Since I have a Usb-soundcard connected directly to my computer which works 100%, I'm a little worried about suspending "all usb-devices".


Thanks for the quick answer.

---

### Post by ddrichardson on 2009-07-10
> **b166er said:**
> Sorry
Whilst I know some about Linux, I've never had problems with USB. So I don't know much about usb stuff.

So how can I get module names?

And looking at that command, Wouldn't that just tell it to suspend the device? I want it to not suspend. Or alternatively make sure the device does wake up.

Does "ath5k" mean the usbcore?.
Since I have a Usb-soundcard connected directly to my computer which works 100%, I'm a little worried about suspending "all usb-devices".


Thanks for the quick answer.Ath5k is the Atheros WiFi driver, this module is suspended during suspend because its in that file, which makes it be reinserted on wake as opposed to leaving it to PM to handle.  I have the same issue but with WiFi - it doesn't come back on resume otherwise.

```
SUSPEND_MODULES="usbcore"
```

Try it first by removing them then suspending:```
sudo modprobe -r usbcore
```

lsmod tells you whats running and it might be worth trying uhci_hcd and ehci_hcd first, infact if you use dmesg to see which the soundcard is on it must be the other.

---

### Post by b166er on 2009-07-10
Ok I see.

Well I used dmesg and found that the hub was on ehci_hcd and the soundcard on uhci_hcd.

But when I tried

SUSPEND_MODULES="ehci_hcd"

Stuff went a little crazy. I could suspend, But the Wacom didn't suspend.
So I had to unplug and replug the hub anyway.

But can I add several "suspend_modules"?. I'm thinking maybe add one for the keyboard and one for the mouse and wacom and so on. although I Don't know what to wright then. Maybe you can see it from this:
```

[  351.024609] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.1/1-2.1.1/1-2.1.1:1.0/input/input10
[  351.034798] logitech 0003:046D:C517.0006: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.7-2.1.1/input0
[  351.040756] logitech 0003:046D:C517.0007: fixing up Logitech keyboard report descriptor
[  351.041617] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.1/1-2.1.1/1-2.1.1:1.1/input/input11
[  351.060129] logitech 0003:046D:C517.0007: input,hiddev96,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-2.1.1/input1
[  351.132308] usb 1-2.1.2: new full speed USB device using ehci_hcd and address 13
[  351.232525] usb 1-2.1.2: configuration #1 chosen from 1 choice
[  351.232984] input: Wacom Intuos3 6x11 as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.0/input/input12
[  351.320310] usb 1-2.1.3: new low speed USB device using ehci_hcd and address 14
[  351.428385] usb 1-2.1.3: configuration #1 chosen from 1 choice
[  351.443569] input: Dell Dell QuietKey Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.1/1-2.1.3/1-2.1.3:1.0/input/input13
[  351.452083] generic-usb 0003:413C:2106.0008: input,hidraw3: USB HID v1.10 Keyboard [Dell Dell QuietKey Keyboard] on usb-0000:00:1d.7-2.1.3/input0
[  351.524296] usb 1-2.1.4: new low speed USB device using ehci_hcd and address 15
[  351.620502] usb 1-2.1.4: configuration #1 chosen from 1 choice
[  351.622727] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.1/1-2.1.4/1-2.1.4:1.0/input/input14
[  351.636762] generic-usb 0003:046D:C018.0009: input,hidraw4: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.7-2.1.4/input0
```

---

### Post by ddrichardson on 2009-07-11
They're space seperated:```
SUSPEND_MODULES="uhci_hcd ehci_hcd"
```Has the Wacom not got its own module?```
lsmod | grep wacom
```

---

