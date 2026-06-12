---
title: "Complicated missing disk space (not in trash)"
date: 2009-07-14
forum: General Help
---

### Post by dontcarefilmer on 2009-07-14
Hi, I've spent the last hour and a half scouring the forums and Google for an answer but I can't find what I need.

Basically what has happened is I wanted to free up disk space so I deleted about 75Gb worth of files (from a single folder). To do this I used nautilus and navigated to the folder. Clicked on the folder containing the files and pressed Shift + delete. After confirming it started to remove the files.

Then the computer froze and nothing was happening, I let it go for a while to see what happens, but nothing. I restarted the pc, only to find that the files were gone but the disk space had not been recovered.

I've already checked and emptied all the trash from my account and root. Ran a variety of disk space commands to find the missing files but with no luck.

If anyone knows what I can do please help.

---

### Post by michy99 on 2009-07-14
Try running fsck on the partition, BUT MAKE SURE IT IS NOT MOUNTED when you run it. Running fsck on a mounted partition will mess it up.

---

### Post by dontcarefilmer on 2009-07-15
Thanks for the quick reply, just ran 'fsck' from the live disk:

ubuntu@ubuntu:~$ sudo fsck.ext4 -f /dev/sda5
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 194295/18210816 files (3.0% non-contiguous), 41998475/72826653 blocks


Unsure if this helps, but it looks like all is well?
By which I mean fsck found no error.

---

### Post by dontcarefilmer on 2009-07-15
I checked the disk usage analyzer to find out if anything has changed and it has found all my missing space. Just rebooted and my installed ubuntu confirms it, all my space is back!

I don't know what happened but it is all fixed. Thanks for your help but. I feel stupid for even asking now, should have rebooted one more time. 

But it makes me wonder why it's come back, after all I didn't really do much. Anyway, thanks again.

---

