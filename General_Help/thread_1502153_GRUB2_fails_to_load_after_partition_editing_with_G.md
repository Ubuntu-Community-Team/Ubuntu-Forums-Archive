---
title: "GRUB2 fails to load after partition editing with GParted"
date: 2010-06-05
forum: General Help
---

### Post by chemicalrubber on 2010-06-05
After resising a HFS+ and an ext4 partition in GParted using an Karmic live cd, GRUB2 fails to load. It was installed as part of Lucid and the computer uses a GUID partition table. OS X was installed the HFS+ partition which booted off the EFI partition. GRUB2 was presumably installed in sda4 (ext4 partition) since there was no MBR. But after partition editing, GRUB2 fails to load. Please help!

---

### Post by Leppie on 2010-06-05
please post the full results of the boot info script: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

