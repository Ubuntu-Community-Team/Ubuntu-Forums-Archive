---
title: "Backing up files changes permissions"
date: 2010-05-14
forum: General Help
---

### Post by trpnblies7 on 2010-05-14
I did a clean install of 10.04 over the weekend and copied all of my backed up files from my external drive back to my internal drive. However, I've noticed that when I moved all my files back, they're all now marked as being executable. I've since fixed this, but I was wondering why this happened to begin with?

I use rsync to backup my files (grsync to be exact), but when I do so I copy files from my internal drive, which is formatted as ext4, to my external drive, which is formatted as NTFS (I keep my external drive as NTFS in case I need to hook it up to a Windows machine). Does the file system discrepancy have to do with why my permissions change when I backup/restore my files? Is there a way to prevent this? Or should I be backing up my files a different way?

Any help is appreciated. Thanks!

---

### Post by Dennis N on 2010-05-14
The file permissions aren't retained when transferred from Linux to the Windows file format. When transferred back from the USB drive to the Linux Computer you are seeing the default permissions that are assigned.

---

