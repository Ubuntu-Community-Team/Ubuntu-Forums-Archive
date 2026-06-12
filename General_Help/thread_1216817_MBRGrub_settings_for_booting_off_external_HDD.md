---
title: "MBR/Grub settings for booting off external HDD"
date: 2009-07-18
forum: General Help
---

### Post by naklinaam on 2009-07-18
Here is my situation:
I have  Windows XP Desktop that I installed ubuntu on in dual boot mode. lets call this drive CDRIVE)
I later installed ubuntu on an external HDD (lets call LINUXUSB)
and I have another extrnal drive that has most of my data on (lets call this DATAUSB).

What I want to do is:
If I plug in he LINUXUSB into my USB hub/desktop and boot the machine, the system should boot into LINUXUSB, which alreay gives me an option of booting into the os on the usb, or the ubuntu on CDRIVE or my native XP itself)

If I do not plug in the USB, it should boot into CDRIVE and give me the option for ubuntu or XP.

Sonuds easy and works most of the times. Now here are the specific issues I need help addressing:

1. If I have DATAUSB plugged in at the time of booting, the system always tries to boot from this drive and fails since this drive is not bootable. This is irrespective of my bios settings

2. Once I remove this drive and restart, the system goes to CDRIVE even if LINUXESB is hooked up. I need to change my BIOS settings and reboot a couple of times before the systems starts booting from LINUXUSB again.

The potential solution I have in mind is to perform 2 actions:
1)make DATAUSB also bootable and in the boot menu let me choose either LINUXUSB, CDRIVE Linus or CDRIVE XP. Thus, even if I forget to pull this device out beforere booting, I can still recover to my OS of choice (LINUXUSB)
2) modify the boot menu of CDRIVE to also give an option of booting into LINUXUSB. Thus even if the system failed to detect LINUXUSB as the USB drive to boot into I can still recover and boot into that install.

So,
Does anyone know how I can achieve this?
Can someone suggest a better solution?

---

