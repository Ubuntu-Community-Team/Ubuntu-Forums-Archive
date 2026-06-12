---
title: "Formating USB stick to FAT32"
date: 2010-01-30
forum: General Help
---

### Post by RadicalApex on 2010-01-30
Hello guys! I have been playing around with ubuntu checking out the different things it can do, and recently I am attempting to format an old thumbdrive to FAT32. So I installed Gparted and created a partition table for the drive, then told it to format to FAT32 but I keep getting an error. I looked into the details of the operations Gparted is doing and it is failing at the point where it is trying to format as FAT32 does anybody have any suggestions?

---

### Post by Leppie on 2010-01-30
what is the exact error/message gparted is showing?

---

### Post by Revolutionary101 on 2010-01-30
Did you delete the original partition before you tried to format it to FAT32?

---

### Post by RadicalApex on 2010-01-31
Nevermind I just figured out what was wrong, I forgot to unmount the disk before formatting. Thanks for the replies.

---

### Post by Leppie on 2010-01-31
if this is solved, then set the thread to solved using the "Thread Tools"

---

