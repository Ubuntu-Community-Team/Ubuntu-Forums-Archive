---
title: "Plz help cannot boot from external dvd"
date: 2011-02-18
forum: General Help
---

### Post by HeZ on 2011-02-18
Hi is it possible that Ubuntu can affect my laptop booting from dvd. I used my external dvd drive to install ubuntu onto my ASUS N10JC, but now when i try to boot from the dvd drive it wont let me? I have boot device #1 set to dvd/cd rom and #2 set to Removable Device, everything else disabled. The drive boots on other computers including a Win7 and a gentoo. Could this be Ubuntu related or just something weird?

Thanks
HeZ

---

### Post by megabuffen on 2011-02-18
Does it boot the hard drive even though you disabled it? If that is the case, check that BIOS settings have been saved correctly.

Anyway, at some point during the initial startup, you should be able to press a key (Enter, F1-12 or something) to manually select a boot device. This should show up on your monitor briefly. If this doesn't work, you might want to try using a standard S-ATA or IDE internal DVD drive.

Also, I think that  selecting DVD/CD ROM in the boot order will tell the BIOS to use an internal drive. An external DVD drive might be called something else, probably with 'USB' in the name. It might even be treated as an external hard drive, USB memory stick or whatever. Try different available options.

Ubuntu should not affect boot devices. It seems to be a BIOS issue.

---

