---
title: "Recovering contents of /home on old disk"
date: 2010-10-16
forum: General Help
---

### Post by MrMetabolism on 2010-10-16
Hey everyone,

I'm usually a Windows user, but I've been working on a uni project in Ubuntu and as luck would have it, the laptop's died a week before the due date.

The hard disk however is fine, but I need to retrieve some files that were in the /home/user/ directory. I figured (as would be the case in windows) that I could just plug the disk in, find the folder, and copy the files onto the new disk. BUT....I can't seem to find the directory anywhere on the disk.

The computer was running Ubuntu 10.04 alongside a windows installation, I used wubi to install ubuntu.

Anyway, any advice that anyone could give that might help me retrieve these files would be greatly appreciated. 

Thanks.

---

### Post by Megaptera on 2010-10-16
You said Wubi install and not dual-boot so, have you tried using Ubuntu as a live CD to rescue your files?

Guide here:  [http://www.makeuseof.com/tag/how-to-back-up-data-on-your-computer-that-wont-boot/#more-32771](http://www.makeuseof.com/tag/how-to-back-up-data-on-your-computer-that-wont-boot/#more-32771)

---

### Post by bcbc on 2010-10-16
Your /home is within a virtual disk, usually root.disk unless you created a separate home.disk. You can find it in the \ubuntu\disks\ directory.

To access the files you can either install ext2read v2.2 (point it at the .disk file) to view from Windows, or loop mount the file from a live CD:
sudo mount -o loop /mountpoint/ubuntu/disks/root.disk /mnt

---

### Post by MrMetabolism on 2010-10-16
Thanks for the replies. I went the ext2read route, all good now.

Cheers.

---

### Post by Megaptera on 2010-10-16
Glad to read you solved it!

---

