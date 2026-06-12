---
title: "Booting Windows installer CD from GRUB"
date: 2011-01-08
forum: General Help
---

### Post by halfbeing on 2011-01-08
I need to boot into a Windows XP installer CD from GRUB. How can I do this?

(The reason is that I need to use drivemap to install to a secondary hard drive.)

Are there any viable workarounds? For instance would installing to the primary disk, copying to the other disk, and then using chainloader to point directly to ntldr work?

Many thanks.

---

### Post by efflandt on 2011-01-08
Wouldn't it be easier to rearrange your drives, so the Windows drive is sda (where it likes to be), with Ubuntu on sdb.  Install Windows on sda, then switch boot order in BIOS to boot grub on sdb.  That way you do not have to worry about Windows or any naughty Windows programs storing data in the mbr of the Windows drive because you would not even be booting from that drive.  That is what is nice about Linux UUID's which can find partitions regardless of which drive they are on.

Just as an example, my new Dell PC has Win7, but Dell DataSafe stores data in what it thinks is an unused part of the mbr.  But grub2 is larger than the Windows mbr, so that steps on grub making it unable to boot.  So in that case I had to put grub2 on a primary partition on sda for Maverick and restore the standard Windows mbr on sda.  Although, I am currently booting Natty on sdb (or Maverick, or Win7 on sda) from Natty's grub2 on sdb.

---

