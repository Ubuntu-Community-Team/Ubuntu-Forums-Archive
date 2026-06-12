---
title: "Problem with saa7130 tv tuner..."
date: 2006-04-29
forum: General Help
---

### Post by chicken101 on 2006-04-29
Hi all, I'm new to linux (running dapper beta 2 at the moment), and I'm having a hard time getting my saa7130 tv tuner to work...

Things I have tried:

1)ran modprobe saa7134
2)dmesg, and found that my tuner card appears as unknown/generic (meaning that the driver isn't loaded).
3) rmmod saa7134, it couldn't unload the driver b/c it was being used by saa7134_alsa.

Another problem I have is all programs that use gstreamer or use openal (like ut 2004) think my tv tuner is my defualt alsa device, so I get no sound.  Hopefully I can get my tv tuner configured right, and that problem with be fixed.  

The saa7134 related output from the dmesg is:

[4294684.641000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> I RQ 185
[4294684.642000] eth0: Identified chip type is 'RTL8169s/8110s'.
[4294684.642000] eth0: RTL8169 at 0xf8882b00, 00:11:09:88:82:d8, IRQ 185
[4294684.741000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4294684.741000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> I RQ 193
[4294684.741000] saa7130[0]: found at 0000:00:06.0, rev: 1, irq: 193, latency: 3 2, mmio: 0xcfffbc00
[4294684.741000] saa7130[0]: subsystem: 1131:2341, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294684.741000] saa7130[0]: board init: gpio is 5d31ff
[4294684.862000] saa7130[0]: i2c eeprom 00: 31 11 41 23 08 20 1c 55 43 43 a9 1c55 43 43 a9
[4294684.862000] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 3731 33 30 20
[4294684.862000] saa7130[0]: i2c eeprom 20: 41 41 48 53 ff ff ff ff ff ff ff ffff ff ff ff
[4294684.862000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ffff ff ff ff
[4294684.862000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ffff ff ff ff
[4294684.862000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ffff ff ff ff
[4294684.862000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ffff ff ff ff
[4294684.862000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ffff ff ff ff
[4294684.862000] saa7130[0]: registered device video0 [v4l2]
[4294684.862000] saa7130[0]: registered device vbi0
[4294685.082000] Real Time Clock Driver v1.12
[4294685.159000] FDC 0 is a post-1991 82077
[4294685.229000] saa7134 ALSA driver for DMA sound loaded
[4294685.229000] saa7130[0]/alsa: saa7130[0] at 0xcfffbc00 irq 193 registered as card -1


Cheers!

---

### Post by danko on 2006-04-30
Sound problem you can "resolve" by adding line "blacklist saa7134_alsa"  to  "/etc/modprobe.d/blacklist" file. The problem occurs because saa7134 driver is loaded before real sound card driver, and /dev/dsp is assigned to it. I suppose this driver is newly added to default Dapper kernel to enable getting saa7134 sound through PCI bus. If this driver is disabled you can get sound in the old manner, with the cable bridge between TV card audio output and sound card input. Of course, you can also change default sound device in Gnome (I do not know how, I am using KDE) or write a script to reload modules in different order, but I think it's not worthed.

---

