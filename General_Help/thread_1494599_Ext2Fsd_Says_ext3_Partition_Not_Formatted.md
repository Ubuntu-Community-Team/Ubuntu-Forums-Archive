---
title: "Ext2Fsd Says ext3 Partition Not Formatted"
date: 2010-05-27
forum: General Help
---

### Post by Ubuntist on 2010-05-27
Dual booting Ubuntu and XP, I've been using ext2fsd for a long time.  Recently I did a fresh install of Lucid.  Now when I try to run ext2fsd from XP, it tells me that my ext3 partition needs to be formatted.  I vaguely recall having had and solved this problem in the past, but I just can't find the solution.  Could anybody lend me a hand?

---

### Post by dcstar on 2010-05-27
> **Ubuntist said:**
> Dual booting Ubuntu and XP, I've been using ext2fsd for a long time.  Recently I did a fresh install of Lucid.  Now when I try to run ext2fsd from XP, it tells me that my ext3 partition needs to be formatted.  I vaguely recall having had and solved this problem in the past, but I just can't find the solution.  Could anybody lend me a hand?

Ubuntu uses EXT4 partitions as default, not EXT3.

---

### Post by Ubuntist on 2010-05-28
OOPS!  Now that you mention it, I remember reading about that somewhere, but I forgot about it while installing Lucid and didn't pay enough attention to what I was doing.

Is there any way I can change my install from ext4 to ext3 without re-installing?

---

### Post by Sef on 2010-05-28
>  Is there any way I can change my install from ext4 to ext3 without  re-installing?

You would have to reformat the ex4 partition and by doing so, wipe out your data.  So, in short, no.

---

### Post by Nythain on 2010-05-28
not to mention that later versions of ubuntu tend to use 256 byte inodes and last i checked, ext2fs only supports 128 byte inodes

---

### Post by Ubuntist on 2010-05-28
> **Sef said:**
> You would have to reformat the ex4 partition and by doing so, wipe out your data.  So, in short, no.

I installed all of Lucid to a single ext4 partition.  Would it be possible for me to shrink the ext4 partition and create a new ext3 partition to which I would move /home?  After all, it's only the stuff in /home that I want to access from XP anyway.

---

### Post by Ubuntist on 2010-05-28
> **Nythain said:**
> not to mention that later versions of ubuntu tend to use 256 byte inodes and last i checked, ext2fs only supports 128 byte inodes

I recall having bumped into that problem too in the past.  Somehow I got around it, and I think it may have been the reason I switched to ext2fs from ext2IFS.

---

### Post by lmarmisa on 2010-05-28
Yes. I think that your proposal makes sense. Even you could define an ext2 partition for /home if you have some doubt about the "new" ext3 file system.

I recommend to use a Live CD for moving (or cp -a) your /home directory.

You will need to change your /etc/fstab file adding a line with the new /home partition.

---

### Post by Nythain on 2010-05-28
well ill be, ext2fsd does support it, its that crappy other one that doesnt :P sorry, been a while since i've had a windows install

---

