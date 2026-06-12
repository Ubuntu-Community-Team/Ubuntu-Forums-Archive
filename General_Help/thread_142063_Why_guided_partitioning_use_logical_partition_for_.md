---
title: "Why guided partitioning use logical partition for swap?"
date: 2006-03-09
forum: General Help
---

### Post by hell0un1verse on 2006-03-09
Hi there, 

I just noted that if you do a "erase entire disk" in Breezy's guided partitioning, it'll create a single primary root partition and a logical partition for swap area, is there any reason for doing so instead of creating a primary partition for swap area?

Thanks.

---

### Post by lamego on 2006-03-09
By definition a primary partition should be used for the operative system, so it makes no sense in making the swap area primary.

---

### Post by hell0un1verse on 2006-03-09
OK. Thanks. I just wonder if there's any performance concern here.

---

### Post by lamego on 2006-03-09
No, despite the different types, they are accessed on the same way: raw disk access.

---

### Post by hell0un1verse on 2006-03-09
I see. Thanks:)

---

