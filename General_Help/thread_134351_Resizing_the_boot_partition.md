---
title: "Resizing the boot partition?"
date: 2006-02-21
forum: General Help
---

### Post by Cephyr on 2006-02-21
So, when I upgraded to Breezy I left my Woody install on the drive. The installer  partitioned the drive about half and half. Now, I've decided that I didn't need my old Woody install so I erased the partition so it's free space. Now I just don't know how to make my main partition (with Breezy) resized so it takes up the free space that used to be my Woody partition.

Thanks!

---

### Post by aysiu on 2006-02-21
You add space to only the **end** of a partition, not the beginning.

So if it's Woody and then main, you can't do much about that. Maybe create a data partition with it?

If it's main and then Woody, just delete Woody and use a live CD to resize your main partition.

---

### Post by queenorych on 2006-02-22
backup
boot off ubuntu live
run gparted

---

### Post by Cephyr on 2006-02-22
Well, it's Woody then Breezy so that doesn't look like that's going to be an option.

So, can I perhaps use that empty space to store files? I'd like to use it to store my music, as that's whats eating up my file space as it is.

---

