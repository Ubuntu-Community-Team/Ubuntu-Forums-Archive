---
title: "windows partition viewing"
date: 2010-03-06
forum: General Help
---

### Post by flyingsliverfin on 2010-03-06
ive been dual booting ubuntu and windows for a while now. For the first time in weeks ive booted windows XP, and i really hate the fact that windows explorer can't read more than the first partitions. Is there a way to make the explorer see more? I want to be able to reach my files on the ubuntu partition from windows, not just the other way

---

### Post by huangweiqiu on 2010-03-06
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) I think this thread has the answer.

---

### Post by MooPi on 2010-03-06
Do a search for Windows ext3 support. Should turn up several pages of useful support. Lots of utilities out there.

---

### Post by DawieS on 2010-03-06
Windows XP can read beyond the first partition. It is more a question of the type of file-systems used in the Ubuntu partition, that XP is unable to read, most likely ext3 or ext4 in your case.

If you are dual booting, and want to be able to directly use data for both XP and Ubuntu, you would need to store it in a partition with a type of file-system that is compatible to both, in this case NTFS.

It is always good practice to store your data separately from your operating systems, in a different drive or partition. That way you can protect it better by keeping it unmounted, or switched off, when not required. Also, the next time you upgrade or reload your OS, you can wipe the old OS, by formatting the partition in which it was installed, without losing any of your data - Be sure to first copy any configuration data, that you may want to use later, out to your data partition.

In your case I would recommend:
- 20 Gb NTFS partition for XP and temporary storage.
- 20 Gb Ext3 or Ext4 partition for Ubuntu and temporary storage.
- 320 Gb NTFS partition for Data (permanent storage).

If you have 2 Gb or more RAM installed, I would not bother with a Swap partition, as Ubuntu would run just as fast without it.

---

### Post by flyingsliverfin on 2010-03-06
i also need to be able to reach my 3rd partition of my usb drive which is fat32...

---

