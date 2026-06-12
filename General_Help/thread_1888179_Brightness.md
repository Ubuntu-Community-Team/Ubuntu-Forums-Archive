---
title: "Brightness?"
date: 2011-11-28
forum: General Help
---

### Post by Egregious on 2011-11-28
Hello all, I've just got a quick question. How would I go about changing the brightness on ubuntu. I'm currently running 11.04 and my FN key for brightness doesn't actually do anything to the display.

Thanks,

Egregious.

---

### Post by gman16000 on 2011-11-28
are you able to adjust the brightness at all??  the first step might be to open up the power center and make sure you can adjust the brightness.

i think this will work in 11.04.  from a terminal:
```
gnome-control-center screen
```

---

### Post by Egregious on 2012-01-10
Sorry this is so much later in time, 


I cant change the brightness at all via power options, any idea why?

Thanks,

Egregious

---

### Post by Toz on 2012-01-10
> **Egregious said:**
> Sorry this is so much later in time, 


I cant change the brightness at all via power options, any idea why?

Thanks,

Egregious
Need more information.
What is the make/model of your computer?

What video card do your have? Open a terminal window, type in the following command, and post back the results:
```
sudo lspci -vnn | grep -A10 VGA
```

Are you using any special kernel parameters?
```
cat /proc/cmdline
```

Do you have a backlight interface?
```
ls /sys/class/backlight
```

---

### Post by Egregious on 2012-01-14
make/model:
acer aspire 5740-5515
processor - i3 2.2ghz

What video card do your have?
```
sudo lspci -vnn | grep -A10 VGA
```
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:033e]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

```

Are you using any special kernel parameters?
```
cat /proc/cmdline
```
```

BOOT_IMAGE=/vmlinuz-2.6.38-11-generic-pae root=UUID=533eb297-40a2-4388-8214-0494d70d7184 ro quiet splash vt.handoff=7

```

Do you have a backlight interface?
```
ls /sys/class/backlight
```
```
acpi_video0
```

---

### Post by Egregious on 2012-01-14
And just in case it matters, i'm running x86 ubuntu

---

### Post by Toz on 2012-01-14
Ok. Lets try the easy stuff first. Can you try the following kernel parameters (one at a time)?

- **acpi_osi=**
- **acpi_osi=Linux**
- **acpi_backlight=vendor**
- **acpi_osi=Linux acpi_backlight=vendor**

For information on how to test these settings, have a look at:[https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

---

