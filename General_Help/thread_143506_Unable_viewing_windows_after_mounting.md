---
title: "Unable viewing /windows after mounting"
date: 2006-03-12
forum: General Help
---

### Post by hikmat on 2006-03-12
Sequence:
--------------

1. Converted my windows partition from ntfs to fat32
2. Inserted following line into my /etc/fstab:

       /dev/sda2       /windows        ntfs   nls=utf8,umask=0222 0 0
3. Saved and was able to enter and view /windows after mounting /dev/sda2 to the /windows directory.

4. Decided to change my windows partition back to ntfs.
5. After, I was able to mount sda2 to the /wiindows directory, but once this is done, /windows becomes read only, with no viewing privileges to myself as a user.

6. I could only view it as root in terminal view, since as root I cannot be in graphical mode.

What has gone wrong, should I revert my windows partition to fat32?

---

### Post by hikmat on 2006-03-12
[QUOTE=hikmat]Sequence:
--------------

1. Converted my windows partition from ntfs to fat32
2. Inserted following line into my /etc/fstab:

       /dev/sda2       /windows        ntfs   nls=utf8,umask=0222 0 0
3. Saved and was able to enter and view /windows after mounting /dev/sda2 to the /windows directory.

4. Decided to change my windows partition back to ntfs.
5. After, I was able to mount sda2 to the /wiindows directory, but once this is done, /windows becomes read only, with no viewing privileges to myself as a user.

6. I could only view it as root in terminal view, since as root I cannot be in graphical mode.

What has gone wrong, should I revert my windows partition to fat32?[/QUOTE]


This is what I did, as I thought I couldn't do any harm. I deleted the avove line from the fstab file, and reinserted it. 
Don't ask me how or why, but it worked. This time, even better. Not only I can go into the /windows directory, but sda2 gets mounted on /windows at startup.

Right now, if it ain't broke, don't fix it, I guess.

---

