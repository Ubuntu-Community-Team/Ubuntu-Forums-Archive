---
title: "USB problem"
date: 2006-06-07
forum: General Help
---

### Post by mlho on 2006-06-07
Can anybody shed some light on this?

When I plug in my USB keyboard, which incidentally doesn't work, dmesg output goes mad. I get several hundred lines of the same thing (see below).

All of these several hundred lines are continuously appended to various system logs, including *kern.log*, *messages* and *syslog*, so much so that each of the these 3 logs have ended up >650Mb, completely filling my root partition which stopped me from logging in.

What I'm trying to find out is:[LIST=1]
[*]What is hid-core.c?
[*]What is irq status -32?
[*]Why is my keyboard generating these messages continuously?
[*]How do I clear the system logs? My 6Gb root partition is about 80% full and it isn't software that is taking up the space! I deleted the three main culprits mentioned above which freed 1.8Gb, but there seem to be other logs lurking around.
[/LIST]

```
[4298339.956000] drivers/usb/input/hid-core.c: input irq status -32 received
[4298339.964000] drivers/usb/input/hid-core.c: input irq status -32 received
[4298339.964000] drivers/usb/input/hid-core.c: input irq status -32 received
[4298339.972000] drivers/usb/input/hid-core.c: input irq status -32 received
[4298339.972000] drivers/usb/input/hid-core.c: input irq status -32 received
[4298339.980000] drivers/usb/input/hid-core.c: input irq status -32 received
[4298339.980000] drivers/usb/input/hid-core.c: input irq status -32 received
  :
  :

```

---

### Post by mlind on 2006-06-07
Kernel is reporting error message constantly, which seems to clutter the logs,
and logrorate cronjob doesn't seem to care about their size.

usbhid module seems to be in control of my mouse. If it's missing, my Logitech
USB mouse doesn't work. 

This looks like a IRQ related problem, which you can sometimes circumvent by
using kernel boot parameters
```

**acpi=off noapic**

```

Try adding these to /boot/grub/menu.lst file, on line which looks like
# defoptions=quiet splash 

modify it to
```

# defoptions=**acpi=off noapic nosplash**

```

save file and run
```

sudo update-grub

```

Boot and see if problem persists.


You should report this problem to Ubuntu launchpad
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bugs](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bugs)




/edit
You can test usbhid module by removing it from running kernel, and adding back again.

To remove, use
```

sudo modprobe -r usbhid

```

and to add back again,
```

sudo modprobe usbhid

```

See if removing stops the messages. And could you post output of
```

lsmod | grep usb

```

---

### Post by mlho on 2006-06-08
I tried the Grub changes, but that didn't make much difference. Like some of the other people who have had the problem, the keyboard works fine up to and including the Grub menu.

If the keyboard is plugged in at boot-up, the loading-up sequence starts, but once it gets round to configuring the keyboard, hundreds of the original IRQ error messages starting appearing (*drivers/usb/input/hid-core.c: input irq status -32 received*, ad infinitum)

If the keyboard is not plugged in at boot-up, I can boot up normally with no major problems. If I go into terminal and type **modprobe -r usbhid**, then **dmesg output |tail** shows this:
```

[  283.451455] usbcore: deregistering driver usbhid
[  283.466439] usbcore: deregistering driver hiddev
[  294.892977] usb 1-2: USB disconnect, address 3
```

If I plug the keyboard in at this stage, the next lines in dmesg are:
```
[  323.956751] usb 1-1: new low speed USB device using uhci_hcd and address 4
[  324.118153] input: USB-compliant keyboard as /class/input/input7
[  324.437202] input: USB-compliant keyboard as /class/input/input8
[  324.437780] usbcore: registered new driver usbkbd
[  324.437939] drivers/usb/input/usbkbd.c: :USB HID Boot Protocol keyboard driver
[  324.463859] usbcore: registered new driver hiddev
[  324.465161] usbcore: registered new driver usbhid
[  324.465392] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

```

The USB keyboard then works. Or at least the basic functions do; the multimedia functions which used to work with Breezy don't, but that's not the end of the world.

And on re-connecting mouse, this:
```
[  359.875598] usb 2-2: new low speed USB device using uhci_hcd and address 3
[  360.032239] input: USB Mouse STD.   as /class/input/input9

```

Unfortunately, when I reboot, the problem simply re-occurs! None of the dmesg output mean much to me. Any ideas what is going on?

As requested, **lsmod |grep usb** gives:
```
usbhid                 38368  0
usbkbd                  7040  0
usb_storage            74176  1
scsi_mod              139496  5 sg,sd_mod,sr_mod,sbp2,usb_storage
usbmouse                5504  0
usbcore               129668  6 usbhid,usbkbd,usb_storage,usbmouse,uhci_hcd

```

---

### Post by mlind on 2006-06-08
I suggest you to file a bug report on Launchpad. IRQ routing for devices at
boottime is failing, but seems to succeed after all other devices have got their
own IRQ. 

You could probably load USB module for keyboard later, but it would not be good
fix for this issue.

Have you tried this by unplugging other USB peripherals and just leave your
keyboard connected? Did you try it on other USB port? If you have APIC or ACPI
settings on your bios, try disabling them.

---

### Post by mlho on 2006-06-09
okay, i have logged it at:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49206](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49206)

switching USB ports doesn't make much difference. i have an in-built smartmedia drive which cannot be physically removed.

mark

---

