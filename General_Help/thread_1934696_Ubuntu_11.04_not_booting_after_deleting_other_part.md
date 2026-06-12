---
title: "Ubuntu 11.04 not booting after deleting other partition"
date: 2012-03-02
forum: General Help
---

### Post by andrew3 on 2012-03-02
Hello,  I previously had 4 partitions on my computer, in order of on hard drive:

1. NTFS
2. FAT32
3. Linux swap
4. Ext4 (Ubuntu 11.04)

However, they weren't in that order in the partition table (ie. I think the Ext4 was /dev/sda1 maybe).  Anyway, I used GParted to delete the FAT32 partition, so:

1. NTFS
2. Linux swap
3. Ext4

I can load Windows from GRUB2 (as before) but when I load 11.04, it does weird stuff.  

The first time I tried to load 11.04 it came up with the loading screen and nothing happened (for >30 min). Now it comes up with a black screen, besides a blank terminal prompt window (as if it was going to load up).

I have tried booting into a LiveCD and doing grub-install --recheck on it, and it "worked" but didn't do anything. So I'm not sure if it's a GRUB problem in that case.  The ext4 partition seems to be alright since I can still mount it and view the files on the LiveCD. So there is no data loss involved. But I would prefer not to have to reinstall again (although I will if I can't find a solution).

Has anyone else had this situation before? Ideas???

---

### Post by ajgreeny on 2012-03-02
Click on the **boot info script** in my signature and follow the instructions there.  Then copy the RESULTS.txt file back here in code tags (use the # icon in the toolbar ans copy the text between the [ CODE] *copy here* [ /CODE] that appear.

---

### Post by andrew3 on 2012-03-02
(removed, unnecessary)

---

### Post by andrew3 on 2012-03-02
I solved this problem by editing /etc/fstab on my ext4 partition and placing a comment (#) in front of the FAT32 partition.

Thanks for your help anyway. :)

---

