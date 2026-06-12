---
title: "Pagefile XP relationship in resizing NTFS and installing ubuntu"
date: 2009-06-28
forum: General Help
---

### Post by texas.chef94 on 2009-06-28
In googling I see where some folks disable page file either pre or post defrag. Then resize. At that point installing Ubuntu to that unallocated space resulting from resize.
Is there a reason for this, is it a myth. necessary or what.

---

### Post by merlinus on 2009-06-28
In general, the paging file lives at the end of the windows partition, and is unmovable.  Therefore defragging will not touch it, and it makes freeing up space much more difficult.

---

### Post by texas.chef94 on 2009-06-28
> **merlinus said:**
> In general, the paging file lives at the end of the windows partition, and is unmovable.  Therefore defragging will not touch it, and it makes freeing up space much more difficult.

Great what I needed to know. Installing on a new linux user and wanted to be sure before I resized his XP

---

### Post by merlinus on 2009-06-28
Be sure to leave enough room in the win partition so you can not only recreate the paging file, but account for ongoing file fragmentation and subsequent defragging, both of which need empty space.

---

