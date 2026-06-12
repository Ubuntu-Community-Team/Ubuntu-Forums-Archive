---
title: "SATA DVD not found"
date: 2011-07-20
forum: General Help
---

### Post by minornut on 2011-07-20
Greetings!

Apologies for asking what may be another noob question. I have seen similar posted, but not quite the same and the solutions I found didn't fit.

I have an ASRock A330 ION mITX mobo, on which I installed mythbuntu (ubuntu 11.04) from a CD iso running from and external bootable USB DVD burner. (Also dual boot Vista)

All was good: mythTV working, tuned, Freeview HD on HDMI TV :)

Now I want to move that DVD burner into the PC case.
It being an IDE drive and me being a cheapskate, I got an IDE to SATA converter and connected it all up.

I have a 1TB SATAII HDD on "SATA 1" and DVD is now on "SATA 2" on the mobo. Mobo is SATAII

The DVD drive is usable in Vista, but not at all in ubuntu.
If there is a CD in the drive, the system will not finish booting until I eject it.
Lots of ata errors to the alt-f1 console.
 /dev/cdrom1 is there, but empty, even if I put a CD in the drive.

I have tried all-generic-ide and irqpoll in grub2, but no difference.
I have tried "AHCI" mode in BIOS-SATA-settings, but that is worse, so I reverted to "IDE mode"

Note that the original mythbuntu install CD will boot in the DVD drive, but after the initial splash screen it hangs.

Looks like a SATA / ATAPI driver issue?

dmesg output attached.

Please help.

Thanks,
Rob.

---

