---
title: "I have noticed the following two folders appear on external HDDs when I use Ubuntu."
date: 2010-12-15
forum: General Help
---

### Post by Rytron on 2010-12-15
Hi.

I have noticed that the following two folders appear on external hard drives when I use Ubuntu. I don't know if they were created by Ubuntu or if they are only seen by Ubuntu. Is it safe to delete them?

Can anyone shed some light on this?

Strange Folders:
[LIST]
[*]RECYCLER
[*]System Volume Information
[/LIST]

---

### Post by wilee-nilee on 2010-12-15
> **Rytron said:**
> Hi.

I have noticed that the following two folders appear on external hard drives when I use Ubuntu. I don't know if they were created by Ubuntu or if they are only seen by Ubuntu. Is it safe to delete them?

Can anyone shed some light on this?

Strange Folders:
[LIST]
[*]RECYCLER
[*]System Volume Information
[/LIST]


Those are windows files they are not hidden in Ubuntu.

---

### Post by syncmasterpt on 2010-12-15
These folders are used by Windows, because you're external drive is probably in NTFS file system format.

If using these drives on other Window systems, I probably leave these folders alone, albeit the contents of Recycle Bin can be deleted.

---

### Post by Rytron on 2010-12-15
Thanks for the info syncmasterpt & wilee-nilee. Why are these folders created?

---

### Post by NCLI on 2010-12-15
> **Rytron said:**
> Thanks for the info syncmasterpt & wilee-nilee. Why are these folders created?

RECYCLER is there to act instead of the Recycle Bin, since it would otherwise have to copy any files you delete from the external disk to your computers internal disk, which would take a long time when deleting a lot of data.

The System Volume Information folder stores your Windows System Restore points.

---

### Post by Rytron on 2010-12-15
> **NCLI said:**
> RECYCLER is there to act instead of the Recycle Bin, since it would otherwise have to copy any files you delete from the external disk to your computers internal disk, which would take a long time when deleting a lot of data.

The System Volume Information folder stores your Windows System Restore points.

Cheers NCLI. Very well explained. :P

---

### Post by theonetruelord on 2011-01-13
Hi!

I use both Windows and Ubuntu, and I have a separate hard drive on which I keep all my media, which I can access from both operating systems. It's not a massive issue, but is it possible to make Ubuntu automatically hide the two folders Windows creates? Just to help keep things tidy, as they mildly irritate me every time I see them!

Thanks

Nick

---

