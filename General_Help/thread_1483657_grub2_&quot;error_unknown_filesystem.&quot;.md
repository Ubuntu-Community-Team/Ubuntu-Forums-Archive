---
title: "grub2: &quot;error: unknown filesystem.&quot;"
date: 2010-05-14
forum: General Help
---

### Post by hsartoris on 2010-05-14
i have been trying to install android as my third booted os on my eee. i shrunk the size of my windows partition to make another partition for android, and left it unformatted, since the installer has a built in partitioner. i formatted the partition as ntfs using android, and rebooted. grub promptly said "error: unknown filesystem.", and presented me with a grub rescue> prompt. when i reran the android installer, it showed the android partition as being FAT16, and no amount of trying would cause it to be anything else. i tried this: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275), but it didn't work, as any interaction with the filesystem causes the error to appear. gparted will not boot off of a usb, neither will ubuntu, or anything else except for damn small linux. however, it cannot find its own filing system, and dies. is there any way to fix this?

oh, the various tutorials that suggest how to get out of this generally don't work. anything that involves interacting with the file system will not work.

---

### Post by _0R10N on 2010-05-14
You could take a look at this thread

[http://ubuntuforums.org/showthread.php?t=1330995](http://ubuntuforums.org/showthread.php?t=1330995)

Kind regards!

---

### Post by hsartoris on 2010-05-14
thanks _0R10N, but that implies that i'm capable of booting into liveCD mode, which i can't do.

---

