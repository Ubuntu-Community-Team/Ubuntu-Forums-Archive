---
title: "usb drive gets renamed with an appended underscore?"
date: 2009-10-17
forum: General Help
---

### Post by aaronLund on 2009-10-17
So I'll mount my usb drive (it's an ext3 formatted drive) and all's well.  However, if I leave it alone for a few days, I'll come back and try to access my drive and it'll be renamed to "driveName_".

This screws things up.

How do I keep this from happening?

Thanks!

---

### Post by Anxiety35 on 2010-04-30
I know this is old, but this started happening to me when I upgraded to Lucid. The original name is always listed in /media regardless of whether the drive is connected or not. When I actually mount the drive, it's adds an underscore at the end since the original name is already taken.

This messes up links and shortcuts I have set up. How can I remove the old hard drive listings from /media? I checked fstab and they weren't listed there.

edit: I solved it by removing those directories.
> sudo rmdir /media/hddName

---

