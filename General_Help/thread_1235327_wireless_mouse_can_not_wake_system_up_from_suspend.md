---
title: "wireless mouse can not wake system up from suspend?"
date: 2009-08-09
forum: General Help
---

### Post by ysha4171 on 2009-08-09
It is confusing that i can wake system up with  my ps2 mouse and keyboard (click any key or button),  however when it comes to wireless mouse and keyboard, it does not work any more?      My wireless mouse and keyboard works fine in my Ubuntu 9.04 Januty.  :confused::confused:

---

### Post by SoftwareExplorer on 2009-08-09
Maybe your receiver goes to sleep and therefore signals from the mouse don't wake it?

---

### Post by P4man on 2009-08-09
I had the same. Please copy your output of

```
cat /proc/acpi/wakeup
```

Here is mine:

> Device	S-state	  Status   Sysfs node
PCI0	  S4	 disabled  no-bus:pci0000:00
PS2K	  S4	 enabled   pnp:00:07
USB1	  S4	 disabled  pci:0000:00:10.0
USB2	  S4	 disabled  pci:0000:00:10.1
USB3	  S4	 disabled  pci:0000:00:10.2
USB4	  S4	 disabled  pci:0000:00:10.3
EHCI	  S4	 disabled  pci:0000:00:10.4
ILAN	  S4	 disabled  pci:0000:00:12.0
P0P7	  S4	 disabled  pci:0000:00:13.0


What this tells you is that USB devices can't wake up my machine, and the PS2 keyboard can.

You can change this temporarily by typing (for instance):

```

sudo -s
echo USB1 > /proc/acpi/wakeup
```

Its a toggle, so if you repeat the command, it will turn it off again.

Check if it worked:

```
cat /proc/acpi/wakeup
```
> Device	S-state	  Status   Sysfs node
PCI0	  S4	 disabled  no-bus:pci0000:00
PS2K	  S4	 enabled   pnp:00:07
USB1	  S4	 enabled   pci:0000:00:10.0
USB2	  S4	 enabled   pci:0000:00:10.1
USB3	  S4	 enabled   pci:0000:00:10.2
USB4	  S4	 enabled   pci:0000:00:10.3
EHCI	  S4	 enabled   pci:0000:00:10.4
ILAN	  S4	 disabled  pci:0000:00:12.0
P0P7	  S4	 disabled  pci:0000:00:13.0


Put your pc to sleep, and see if your USB device can wake it up.
If it does, Ill help you make the change permanent.

In my case, enabling USB as wakeup event made mouse *movements* wake up my computer which I find undesirable, I havent found a way to make it respond to clicks only...

---

### Post by SoftwareExplorer on 2009-08-09
Thanks p4man, I might even try this on my computer. I always had assumed it was physically impossible, but if it works with wireless keyboards and mice that's pretty cool.

---

### Post by P4man on 2009-08-10
its certainly possible; in S3 or even S4 sleep mode, you can still power USB devices (like the receiver for you keyboard / mouse) or your network card and those devices can generate an interrupt to wake the machine up. What I havent yet found is how to allow one USB device to resume the machine, but not the other, but I haven't looked very far yet :)

---

