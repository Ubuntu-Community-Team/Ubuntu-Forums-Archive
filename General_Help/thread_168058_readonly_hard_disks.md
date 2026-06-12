---
title: "readonly hard disks"
date: 2006-04-29
forum: General Help
---

### Post by pvent on 2006-04-29
My system recognices the NTFS partition in my disk, but doesn't let me change the permissions to it, saying the disk is readonly. How do I make it not readonly?

---

### Post by cgjones on 2006-04-29
Writing to a NTFS partition is possible in Linux, but normally not recommended. What are you trying to do that requires write permissions?

---

### Post by pvent on 2006-04-29
I want to access the NTFS partition as if it was the Ext2 one. I use that partition as a repository (I have Wndows XP installed in a third FAT32 partition), and I want to access that data from both OSs.

---

### Post by cgjones on 2006-04-29
Depending on what is currently on the NTFS partition, I would format it as FAT32. This way, both Ubuntu and Windows can have read/write access to it.

---

### Post by pvent on 2006-04-29
Also, when I try to give write and execute permission to my FAT32 partition, the checkbox would unmark itself immediately, so I can only write in it from the root user, and I want every user (or at least my non-root user) to have full access to that disk too. Any idea why does this happen?

But if it's safer to handle the FAT32 system rather than NTFS, I guess I can convert that partition with Partition Magic or something. Is it safe to convert a 40GB NTFS partition (with like 30GB used) to FAT32?

---

### Post by cgjones on 2006-04-29
Take a look here for information on accessing Windows partitions from Ubuntu.
[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

I certainly wouldn't try converting from NTFS to FAT32. If you could move the data off that partition and then format it from Ubuntu, you could then move the data back.

---

### Post by pvent on 2006-04-29
Ok, thanks, I'll try this out and see what happens.
Too bad I don't have where to store all that data while I convert the disk.

---

### Post by ZylGadis on 2006-04-29
A much better option would actually be to format the partition as ext3 (after you move the data, of course). There is a set of tools (whose name I don't remember unfortunately) for windows that enable accessing ext3 partitions. Search the forums for that.

---

### Post by pvent on 2006-04-29
I already downloaded a patch for Windows that gives me full access to Ext2 partition. Would it work the same way if I formatted it like that? Cause I don't know of if that patch works for Ext3 partitions (that's why I formatted the Linux partition as Ext2 instead of Ext3 in the first place).

---

