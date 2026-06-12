---
title: "Help me with my Dinova keyboard"
date: 2010-07-02
forum: General Help
---

### Post by sentiraz on 2010-07-02
Alright lets get straight to it, i just bought my new Dinovo wireless keyboard from logitech and i was excited to try it out on my ubuntu, but when i plugged it in and tried it it didnt respond ( YES is was charged ) i dont know what to do i might getting a new keyboard but i just wanted some help :( :(

---

### Post by cariboo on 2010-07-02
Is the receiver/transmitter detected when you plug it in? To check open a terminal and type:

```
dmesg | tail -n10
```

just after you have plugged the device in. Paste the output in your next post.

---

### Post by sentiraz on 2010-07-02
> **cariboo907 said:**
> Is the receiver/transmitter detected when you plug it in? To check open a terminal and type:

```
dmesg | tail -n10
```just after you have plugged the device in. Paste the output in your next post.
[ 5015.146045] usb 5-1.3.2: new full speed USB device using uhci_hcd and address 5
[ 5015.295197] usb 5-1.3.2: configuration #1 chosen from 1 choice
[ 5015.305313] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1.3/5-1.3.2/5-1.3.2:1.0/input/input15
[ 5015.305392] generic-usb 0003:046D:C713.000B: input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.2-1.3.2/input0
[ 5015.378038] usb 5-1.3.3: new full speed USB device using uhci_hcd and address 6
[ 5015.527152] usb 5-1.3.3: configuration #1 chosen from 1 choice
[ 5015.543661] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1.3/5-1.3.3/5-1.3.3:1.0/input/input16
[ 5015.543797] logitech 0003:046D:C714.000C: input,hiddev97,hidraw3: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.2-1.3.3/input0
[ 5015.838043] usb 5-1.3.1: new full speed USB device using uhci_hcd and address 7
[ 5015.967205] usb 5-1.3.1: configuration #1 chosen from 1 choice 


thats what it said

---

### Post by sentiraz on 2010-07-02
> **cariboo907 said:**
> Is the receiver/transmitter detected when you plug it in? To check open a terminal and type:

```
dmesg | tail -n10
```just after you have plugged the device in. Paste the output in your next post.
What you think i should do?

---

### Post by unknownsoldierX on 2010-07-03
I have the same problem.  How am I supposed to type any commands when it is the only keyboard I have?

Keyboard works fine in Windows (of course) and Knoppix, yet Ubuntu isn't smart enough to detect a bluetooth keyboard.  We're expected to buy/borrow another keyboard in order to install our keyboard?

---

