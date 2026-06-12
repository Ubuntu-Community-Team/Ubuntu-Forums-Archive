---
title: "Chain boot usb drive?"
date: 2010-08-19
forum: General Help
---

### Post by mooson on 2010-08-19
I have an older net book. It has no CD-drive, no floppy, and no boot from flash drive support. Basically my only options for booting is an external floppy I bought. It does boot from the floppy(i tried to repair xp with it and install that way)

I need to some how boot from the floppy. Get enough on there to either:
1. boot from my flash drive
or
2 boot from a network source?

More info:
Lifebook P series running XP with a missing/corrupt hal.ddl that cant be fixed through XP recovery mode because access is denied.
The machine only has 240MB of ram and a 30GB hdd. I have to identical(one with xp and the other has this problem).

---

### Post by spiky001 on 2010-08-19
Have a look here might be what you need
[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by oldfred on 2010-08-19
Grub floppy.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc)

Plop
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Older use grub to boot USB
[http://64.124.13.3/hacks/USB_Boot_using_GRUB.html](http://64.124.13.3/hacks/USB_Boot_using_GRUB.html)

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by mooson on 2010-08-20
Thanks but none of it works. Ubuntu wont see me floppy drive anymore.

Any ideas how to make a grub floppy from windows?

---

