---
title: "Mouse freeze after a few seconds..."
date: 2012-07-30
forum: General Help
---

### Post by JCM_Pico on 2012-07-30
Hi there every mouse I connect to an USB port gets freeze after a few seconds and I need to click... for it to start moving again....

Mean while I notice something... When the mouse is moving *dmesg* shows this:

```
[  488.256374] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 2 ep 0 with no TDs queued?

```

As soon as the mouse get freezed *dmesg* shows this 

```
[  491.038489] xhci_hcd 0000:00:14.0: PME# enabled
```

When I click and the mouse starts moving the cursor again* dmesg*

```
[  502.032612] xhci_hcd 0000:00:14.0: PME# disabled
[  502.032637] xhci_hcd 0000:00:14.0: setting latency timer to 64
```

Is it possible to turn this off? its really annoying....

---

### Post by JCM_Pico on 2012-07-31
This is really annoying and so far I couldn't fix it. So ...

!!!! BUMP !!!!

---

### Post by JCM_Pico on 2012-07-31
Tried to change some usb preferences... but the problem does not go away 

in the file /etc/usb_modeswitch.conf

changed the option 
```
# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0
```

to
```
# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=1
```


Any suggestion? This is driving me nuts :mad:

---

### Post by eexpress on 2013-07-20
I come across such a situation.

[ 2487.170181] ehci_hcd 0000:00:1d.0: PME# enabled
[ 2487.181922] xhci_hcd 0000:00:14.0: PME# disabled
[ 2487.181950] xhci_hcd 0000:00:14.0: setting latency timer to 64
[ 2487.185891] ehci_hcd 0000:00:1a.0: BAR 0: set to [mem 0xc0719000-0xc07193ff] (PCI addre
[ 2487.185950] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, wri
[ 2487.186022] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000,
[ 2487.186224] ehci_hcd 0000:00:1a.0: PME# disabled
[ 2487.186255] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2487.186274] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 2487.186320] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 2487.186397] ehci_hcd 0000:00:1a.0: PME# enabled

continue move can keep it work.
click or scroll can wake up mouse.
My touchpad works well.
I do not know what is PME module.
this just happened on my Dell XPS-L421X with usb3 port. With system is ubuntu 12.04.
Strange thing.

---

### Post by eexpress on 2013-07-20
according to [https://www.kernel.org/doc/Documentation/usb/power-management.txt](https://www.kernel.org/doc/Documentation/usb/power-management.txt)

uncomfortable method:
&#9679; lsusb
Bus **003** Device 004: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
&#9679; l /sys/bus/usb/devices/3*
/sys/bus/usb/devices/3-0:1.0@  /sys/bus/usb/devices/**3-1**@  /sys/bus/usb/devices/3-1:1.0@
&#9679; sudo su
# echo on >/sys/bus/usb/devices/3-1/power/control

-----------------------------------------------------------------------------------------------------------
want more comfortable, modify one line in certain udev file, but fail:
&#9679; grep 'power/control' /lib/udev/rules.d/*
40-libsane.rules:1179:ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'if test -e /sys/$env{DEVPATH}/power/control; then echo on > /sys/$env{DEVPATH}/power/control; elif test -e /sys/$env{DEVPATH}/power/level; then echo on > /sys/$env{DEVPATH}/power/level; fi'"
42-qemu-usb.rules:11:ACTION=="add", SUBSYSTEM=="usb", ATTR{product}=="QEMU USB Mouse", ATTR{serial}=="42", TEST=="power/control", ATTR{power/control}="**on**"
42-qemu-usb.rules:12:ACTION=="add", SUBSYSTEM=="usb", ATTR{product}=="QEMU USB Tablet", ATTR{serial}=="42", TEST=="power/control", ATTR{power/control}="auto"
42-qemu-usb.rules:13:ACTION=="add", SUBSYSTEM=="usb", ATTR{product}=="QEMU USB Keyboard", ATTR{serial}=="42", TEST=="power/control", ATTR{power/control}="auto"

&#9679; grep 'add.*usb.*mouse' *
42-qemu-usb.rules:11:ACTION=="add", SUBSYSTEM=="usb", ATTR{product}=="QEMU USB Mouse", ATTR{serial}=="42", TEST=="power/control", ATTR{power/control}="on"

-----------------------------------------------------------------------------------------------------------
still fail.
&#9679; cat /etc/udev/rules.d/90-usb-mouse-PME.rules 
ACTION=="add", SUBSYSTEM=="usb", TEST=="power/control", ATTR{power/control}="on"

---

### Post by eexpress on 2013-07-20
this works.

&#9679; g mouse 50-udev-default.rules
24:KERNEL=="mouse*|mice|event*",	MODE="0640", **ATTR{power/control}="on"**

---

