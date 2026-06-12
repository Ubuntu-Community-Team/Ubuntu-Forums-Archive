---
title: "How to repair Ubuntu?"
date: 2009-11-12
forum: General Help
---

### Post by OldGrantonian on 2009-11-12
I have a Vista laptop with an Ubuntu partition.

If the Windows partitions become corrupt, I can use the Windows repair disk (frequently!) :)

But what happens if the Ubuntu partitions become corrupt?

BTW1: No panic! I'm only asking so that I can be prepared :)

BTW2:  I have separate Ubuntu partitions for / and /home. The /home partition is backed up to an external HDD. But what do I do with the / partition?

---

### Post by t4thfavor on 2009-11-12
Thought there was a repair option on the alternate disk. If not, you can usually fix any problem with the liveCD. Also if you have all your data backed up, it only takes a bot to reinstall, and put your software back into place as a last resort.

---

### Post by Mark Phelps on 2009-11-12
> **OldGrantonian said:**
>  ... But what happens if the Ubuntu partitions become corrupt?

Depends on how bad the corruption is.

Ubuntu runs disk checks (fsck) on a routine basis to try and prevent filesystem corruption.

If you can't get to a desktop, you can always boot into a console and run fsck from there.

If you can't boot at all into your installed Ubuntu, you can always boot from a liveCD and run fsck from there.

---

