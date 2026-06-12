---
title: "ata 4: SRST failed (ERRNO=16"
date: 2010-03-17
forum: General Help
---

### Post by nikola43 on 2010-03-17
Trying to get on-board audio to work in Jaunty after new install (was working fine when I had 9.1 installed earlier)-anyway, couldn't get it so I installed a Sound Blaster PCI and tried again-no go-set bios to disable MB audio-still no go. also during this process started noticing on boot that the secondary CDrom disappeared and the boot was much slower and started showing errors; "[some number]: ata 4 SRST failed (ERRNO=16"--it would list this line several times (sometimes with a different bracketed number and a different error number, then would eventually boot. I decided at one point to start over and reinstall (9.04CE) so I set bios to boot CD only-it went thru the motions to the point where the disc sys should boot and gave the same errors instead-eventually it did go to the install screen. BTW, this is all on a MB from an HP presario-A7V8X-LA board w/ Athlon Thunderbird CPU & 512 ram.
My question is: what does the error message mean and is there a way to correct it?

---

### Post by dcstar on 2010-03-17
> **nikola43 said:**
> Trying to get on-board audio to work in Jaunty after new install (was working fine when I had 9.1 installed earlier)-anyway, couldn't get it so I installed a Sound Blaster PCI and tried again-no go-set bios to disable MB audio-still no go. also during this process started noticing on boot that the secondary CDrom disappeared and the boot was much slower and started showing errors; "[some number]: ata 4 SRST failed (ERRNO=16"--it would list this line several times (sometimes with a different bracketed number and a different error number, then would eventually boot. I decided at one point to start over and reinstall (9.04CE) so I set bios to boot CD only-it went thru the motions to the point where the disc sys should boot and gave the same errors instead-eventually it did go to the install screen. BTW, this is all on a MB from an HP presario-A7V8X-LA board w/ Athlon Thunderbird CPU & 512 ram.
My question is: what does the error message mean and is there a way to correct it?

It means there a hardware problem on ATA device 4. Remove the PCI card and see if the problem goes away.

---

