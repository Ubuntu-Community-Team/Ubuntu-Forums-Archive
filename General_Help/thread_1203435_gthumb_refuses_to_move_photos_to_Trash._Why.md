---
title: "gthumb refuses to move photos to Trash. Why?"
date: 2009-07-03
forum: General Help
---

### Post by quixote on 2009-07-03
I have my photo dir on a /mnt/data partition, with a sym link in my home dir.  When I scan through photos in gthumb and want to delete one, it says "The images cannot be moved to the Trash. Do you want to delete them permanently?"  Why???  I know gthumb insists on using "system Trash."  I've tried to find every Trash dir on my system, and chmod to 777, but I still get that message.

Is there any way around this annoyance with gthumb?  It's the best program for labelling photo files as they come off the camera, and sorting through keepers vs deleters.  That's why this is such a big problem for me.  I want to be able to change my mind about deletions!

I run 64-bit Jaunty.

Hope someone can help.

---

### Post by philinux on 2009-07-03
Try opening the files directly from the /mnt/data partition then try deleting a test image. It maybe something to do with the symlink.

---

### Post by michy99 on 2009-07-03
What format is the data partition? If it is FAT32, I don't know if trash will work for it. Can you move files to trash on that partition in nautilus?

---

### Post by philinux on 2009-07-03
> **michy99 said:**
> What format is the data partition? If it is FAT32, I don't know if trash will work for it. Can you move files to trash on that partition in nautilus?

Michy99 is on then money here. since nautils will try to create trash on the data partition. Has to be ext format.

---

### Post by quixote on 2009-07-03
Thanks for the fast replies!

Problem is solved.  ):P

My data partition is ext3, and I tried moving to trash in nautilus (which worked), and moving to trash in gthumb after opening the file from /mnt/data/photos (which didn't).

That made it seem the problem had to be gthumb, but luckily before getting deep into the weeds, I noticed that even though /mnt/data/photos is owned by the user, the data partition itself is owned by root.  That was odd because I'd specifically set up fstab so it could be mounted by user.  

After a short trip to fstab and the man pages, I realized I'd put "users" on that line, not "user", and that there's a difference.  "users" apparently means users can unmount, whereas "user" is for both mounting and unmounting. I changed it to "user", rebooted, and -- ta-da! -- gthumb will now let me trash things on the data partition!

I would have gone on barking up the wrong tree forever without your help.  Thanks!

---

