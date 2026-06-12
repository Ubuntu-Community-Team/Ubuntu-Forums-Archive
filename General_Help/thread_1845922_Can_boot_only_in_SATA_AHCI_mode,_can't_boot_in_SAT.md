---
title: "Can boot only in SATA AHCI mode, can't boot in SATA IDE mode"
date: 2011-09-18
forum: General Help
---

### Post by terrox on 2011-09-18
I have the same error message as this topic [http://ubuntuforums.org/showthread.php?t=981159&page=4](http://ubuntuforums.org/showthread.php?t=981159&page=4) "gave up waiting for root device /dev/sda.." etc.

If I change my BIOS to AHCI mode it will boot all my linux OSes fine, I have about 4.
If I change my BIOS to Standard IDE mode, I get the error above.
Boots to Windows XP fine in IDE mode, wont work in AHCI mode (would need re-install for AHCI drivers).

Linuxes are old-ish, 8.x and such. Booting from some (but not all) modern liveCD will show the drives.
Motherboard is Asus P8H67-M EVO
SATA HDD is connected to SATA-III port. Marvell 88SE6111
Previously was worked fine connected by SATA-I on a different motherboard, and before that the partitions were copied from an IDE HDD, so I know that IDE should work fine as the OSes were all installed on an IDE connection.

Any ideas why IDE wont work in linux?

---

### Post by dcstar on 2011-09-18
> **terrox said:**
> I have the same error message as this topic [http://ubuntuforums.org/showthread.php?t=981159&page=4](http://ubuntuforums.org/showthread.php?t=981159&page=4) "gave up waiting for root device /dev/sda.." etc.

If I change my BIOS to AHCI mode it will boot all my linux OSes fine, I have about 4.
If I change my BIOS to Standard IDE mode, I get the error above.
Boots to Windows XP fine in IDE mode, wont work in AHCI mode **(would need re-install for AHCI drivers)**.
.........

Not really, you can Google simple procedures to install the AHCI drivers post-install in XP (or Vista or Win 7.....).

---

### Post by terrox on 2011-09-18
> **dcstar said:**
> Not really, you can Google simple procedures to install the AHCI drivers post-install in XP (or Vista or Win 7.....).
It isn't that easy as it needs to be registry specific for each controller. But still this is more about Linux failing with IDE mode in my situation.

---

### Post by dcstar on 2011-09-18
> **terrox said:**
> It isn't that easy as it needs to be registry specific for each controller. But still this is more about Linux failing with IDE mode in my situation.

You usually just can't move already installed OSs to totally different hardware without having issues.

The Linux kernels are probably detecting the new IDE mode hardware environment in a totally different way compared to the old motherboard, the AHCI mode probably works because the motherboard BIOS is sticking to the standards a bit more closely.

---

### Post by terrox on 2011-09-18
bummer. I found out I have a Marvell 88SE6111 controller, if that helps anyone in the future.

---

