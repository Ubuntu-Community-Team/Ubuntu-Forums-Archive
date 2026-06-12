---
title: "Lost+Found"
date: 2010-02-27
forum: General Help
---

### Post by ferret man on 2010-02-27
I have just done a fresh install of Ubuntu, and I specified for a separate home partition. The home partition is formatted to ext3 and so is the root partition. I would like to know why both partitions have a Lost+found folder, and what that folder does. And also, is it safe to remove it from the home partition (to free up space)? Thank you very much for taking the time to read this.

---

### Post by Ozymandias_117 on 2010-02-27
Lost+Found is used more from ext2 (although it can in theory still be used occasionaly) When your computer crashed it would do a check of the disk, and anything that could be recovered would be thrown into Lost+Found. It's probably not a good idea to delete it.

---

### Post by ferret man on 2010-02-27
That clears it up. Thank you very much! :o

---

### Post by byStanderone on 2010-02-27
...lost+found is a system folder, primarily used by fsck and can be left alone, but of course you can always delete its content if your storage space is at critical and that you have no other option but to do so.(get a root privelege to do this) ...only often times lost+found folder is empty.

---

