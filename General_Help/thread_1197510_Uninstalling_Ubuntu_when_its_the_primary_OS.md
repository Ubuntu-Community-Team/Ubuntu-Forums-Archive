---
title: "Uninstalling Ubuntu when its the primary OS?"
date: 2009-06-26
forum: General Help
---

### Post by Ubuk2008 on 2009-06-26
Hi guys, I have a problem that I sincerely hope has a solution.

My problem: When I bought my PC I installed Ubuntu as the first OS (i.e. Windows was never installed). Now I want to make completely remove Ubuntu and, perhaps in the future, install Windows.

Is this possible? If so, what steps do I take?

---

### Post by credobyte on 2009-06-26
Boot from your Windows CD and delete Ubuntu partition :)

---

### Post by howefield on 2009-06-26
> **Ubuk2008 said:**
> Now I want to make completely remove Ubuntu and, perhaps in the future, install Windows.

Boot the Ubuntu Live cd and use Partition Editor from the system > administration menu to delete your ubuntu partition / disk and format as required.

---

### Post by Ubuk2008 on 2009-06-26
Thanks for replying. 

What about the GRUB loader? Will that be auto removed?

---

### Post by howefield on 2009-06-28
Yes, formatting the partition will remove grub, but it isn't something to be too worried about because even if it didn't,  installing windows would over write it with the windows bootloader.

---

