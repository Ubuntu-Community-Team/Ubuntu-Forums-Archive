---
title: "Installation Ejects CD-Rom when done.  Can I stop this?"
date: 2010-01-20
forum: General Help
---

### Post by blakelucchesi on 2010-01-20
I'm installing Ubuntu Hardy 8.04.3 LTS Server on a Sun x4150 server.  I'm trying to make it so that when I do a remote install using the ILOM remote console with visual display that the cd-rom is not ejected from the server.  The reason I want to make sure the cd-rom is not ejected is because I can't push it back in for use later if I need to re-install the base system again. 

Is there a way I can run the installation using a command line only option that would then keep the cd-rom from being ejected?

Any thoughts/help would be great.

---

### Post by phillw on 2010-01-20
Hi,

As you are booting from the CD-ROM to do the installation - If it were left in, the computer would boot of CD when you re-booted.

One way round it would be to make a small partition, 1GB - and copy the ISO onto there, that way you'd still have the files after the disk had been ejected.

Others may have a different way, but I can't see a way round booting from the CD for the install & then ignoring it afterwards.

Regards,

Phill.

---

### Post by blakelucchesi on 2010-01-20
Hmm, thanks for the suggestion.  I guess in that case I could probably pick up a usb thumb drive and maybe try installing off of that?  Not sure I like the idea of creating new partitions on the drive just for a ubuntu install cd.  

Also, I was planning on just jumping into the bios after install to boot from HDD instead of the CDRom after install.  Or there is a setting in the Sun ILOM that I can have it override the first boot device for only the next restart, so I would set it as cdrom for the next boot, run the installation, and then it would automatically switch back to the bios default which is the hdd.

--Blake

---

