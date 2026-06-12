---
title: "Grub2"
date: 2009-10-12
forum: General Help
---

### Post by benl11235 on 2009-10-12
Does grub2 support booting off of encrypted partitions( combining /boot and /home. I would like an encrypted system, but only have one partition in the mbr available. Thank you

Edit: Does anyone have ntfs compression working or a howto. I assume it doesnt support compression with different filesystems(hfs+).

---

### Post by benl11235 on 2009-10-13
Grub2 does however support installation on a /boot partition within a lvm group! Now I can run Mac, Windows and Linux(without cutting swap or sacrificing encryption) in just 4 partitions!

---

### Post by carnagex420x on 2009-10-13
I tried installing all 3 before, WOW that wasn't fun. As far GRUB2 its easier to use as a master. If you secure your BIOS and have it boot to only HDD, and secure GRUB. No idea on a encrypted filesystem tho.

---

