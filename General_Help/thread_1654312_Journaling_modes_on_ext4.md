---
title: "Journaling modes on ext4"
date: 2010-12-28
forum: General Help
---

### Post by Sworddragon on 2010-12-28
I have read on many pages the differences between all 3 journaling modes but I'm not sure if I understood all and have now a few questions:

1. What exactly is the metadata? Is it the information about the last access/modifying time, the registered inode and so on?

2. Is data=writeback writing the journal entry first and then the data  to the blocks? Does this even mean that a power failure can corrupt the  data?

3. What is the advantage of data=writeback? Is it only the fast system check after a power failure?

4. data=ordered uses a transaction to prevent data corruption. What is the disadvantage compared to data=journal then? Is there a special way that the data in the ordered mode can be corrupted?

5. data=journal is writing the data first to the journal and then to the blocks. Is the data in the journal deleted after the transaction is completed or is the data kept and I have only the half of the disk space?

5. Can the maximum file size on data=journal only the half of the disk space because the data is written 2 times?

6. Is there any difference between "chattr -R +j /" and mounting the drive directly with data=journal except that the chattr command forces full data journaling on other mounted data options too?

7. I used "chattr -R +s /" too on my file system but I can delete a file that is ~10GB large in a second. Prevents the full data journaling the secure deletion?

---

