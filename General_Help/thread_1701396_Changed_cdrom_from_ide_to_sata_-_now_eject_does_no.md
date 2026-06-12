---
title: "Changed cdrom from ide to sata - now eject does not work"
date: 2011-03-06
forum: General Help
---

### Post by diddy1234 on 2011-03-06
I was wondering how to fix the following problem.

My ide DVD drive stopped working so today I changed it to an sata dvd writer drive.

Only it is seen as /dev/sr0 or /dev/cdrom2

I now have the problem that commands like 'eject' and vobcopy no longer work.

If I type 'eject /dev/sr0' I get the drive to eject

But if I use vobcopy, even with the -i /dev/sr0 this does not work.

This is one thing about Linux (in general) that winds me up if hardware is changed.

Originally I could not even mount the drive as it did not exist in the fstab, so I added :-

#cdrom
/dev/cdrom2 /mnt/cdrom  auto noauto,rw,users    0       0

This seems to work but is that correct ?

So how do I get the new DVD writer drive to work like the original DVD drive ?

Thanks in advance.

---

