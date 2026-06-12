---
title: "Back-up Hard disc format"
date: 2012-05-06
forum: General Help
---

### Post by Hatsune Miku on 2012-05-06
Hello everyone, need a bit of advice. I have a portable HD I would like to use as a backup for my computer. I have a server running Ubuntu 12.04, and have the removable HD plugged into that. Now I will be sending files to the Removable HD to keep back ups and what not. But I do have a question, what format should I make the HD to do the backups on? Should I use NTFS or EXT4? I'll be using this on Linux only machines, thanks for the advice in advance!

And if I do use EXT4, how can I set it to where there are no permissions, or its 100% universally accessible?

---

### Post by Paqman on 2012-05-06
It doesn't really matter. If your sure it's Linux only then use the default, which is Ext4. If there's any chance you might need to access it from a Windows machine, use NTFS.

For universal access under Ext4 just change the permissions so that all files and folders have read/write/execute access. You can either do that on the drive itself, or through a mask in /etc/fstab on the machine you mount it on. Let us know exactly how you'll be using it if you want specific instructions.

---

### Post by Hatsune Miku on 2012-05-06
> **Paqman said:**
> It doesn't really matter. If your sure it's Linux only then use the default, which is Ext4. If there's any chance you might need to access it from a Windows machine, use NTFS.

For universal access under Ext4 just change the permissions so that all files and folders have read/write/execute access. You can either do that on the drive itself, or through a mask in /etc/fstab on the machine you mount it on. Let us know exactly how you'll be using it if you want specific instructions.

To put it simply, That i could plug my back up into a friends computer and he could mount the drive without getting some type of permission lock to read or write to the drive. Basically anyone or anything can accesses and write to the drive without a permission error.

---

### Post by Hatsune Miku on 2012-05-07
Bump

---

### Post by hjclaes on 2012-05-07
Hi,

maybe you should define what you want to do.
Do you want to have a copy of some files or a backup (a backup has a history)? Do you want / have to be able to restore permissions also? Do you want to be able to restore hard links? What do you want to copy / backup? . . .

It may be a good idea also to read this thread which may answer some of your questions:

[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

