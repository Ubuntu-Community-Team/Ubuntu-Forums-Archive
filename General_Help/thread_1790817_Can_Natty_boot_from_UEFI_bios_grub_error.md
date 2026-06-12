---
title: "Can Natty boot from UEFI bios? grub error"
date: 2011-06-25
forum: General Help
---

### Post by nrundy on 2011-06-25
A friend is having trouble booting Natty from the live CD in order to install ubuntu. Grub is giving an error message "Error: prefix not set". or something like that when he tries to boot from the CD.

My friend is speculating that it can't boot because it's an uefi drive. he got a lenovo thinkpad.

---

### Post by srs5694 on 2011-06-25
In theory, Ubuntu 11.04 can install fine on a UEFI-based system. In practice, it's extremely flaky. I have three suggestions:

_Suggestion 1_

Switch the computer to BIOS mode (most UEFI firmwares do have a BIOS boot mode as an option), install that way, install a UEFI-capable boot loader, and reboot in UEFI mode. (Alternatively, if you don't need UEFI mode for, say, GPT support in Windows, you could continue to boot the installed system in BIOS mode.) This may be the best solution.

_Suggestion 2_

Try the following commands, or variants of them, at the grub> prompt:

```

set prefix=(cd0)/boot/grub
set root=(cd0)
insmod normal
normal

```

I'm not 100% certain that "(cd0)" is the correct device name, though. Type "ls" to see what devices are present.

_Suggestion 3_

Try copying the installation files to a FAT-formatted USB flash drive and then installing [ELILO](http://elilo.sourceforge.net) to that drive. You'll need to create an elilo.conf file that references the Linux kernel and initial RAM disk on the USB flash drive. You'll then have to use the UEFI firmware's boot loader to locate and run the elilo.efi file from the USB flash drive.

---

