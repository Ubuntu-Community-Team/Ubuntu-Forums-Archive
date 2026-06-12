---
title: "Linux drive appears empty in windows?"
date: 2010-09-02
forum: General Help
---

### Post by MintPaw on 2010-09-02
This isn't really a linux question but I hope someone will be able to tell me what's going on. Or at least point me at a better place to ask this question.
 
So I have my Windows(For flash Development) an Linux(For everything else) partitions installed and I tryed to install "Ext2Fsd" to Windows so I could view my Linux drive when I'm in windows. (They are both on a different drive.)
 
But when I open it's assigned letter all the folders appear (home, root, etc...) But each one is empty. Any ideas?
 
Thanks in advance.

---

### Post by dv3500ea on 2010-09-02
I've never had much success with the Windows Ext drivers - in fact, I'm pretty sure one gave me a BSOD.

Your best bet would be to use a small (maybe 4GB) partition formatted as FAT32 for sharing files between Ubuntu and Windows.

---

### Post by clrg on 2010-09-02
What filesystem have you formatted your Linux partition with?

---

### Post by linux-hack on 2010-09-02
If you want to see the partition in windows you need to make it NTFS ot FAT32. If not windows will not see the partition or just an empty one.

And if not you can take a look at this :[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by Mark Phelps on 2010-09-02
> **MintPaw said:**
> ... I tryed to install "Ext2Fsd" to Windows so I could view my Linux drive when I'm in windows. (They are both on a different drive.)
 
But when I open it's assigned letter all the folders appear (home, root, etc...) But each one is empty. Any ideas?
 
Thanks in advance.

IF this is a recent Ubuntu version (9.10 or 10.04), and you used the default filesystem (Ext4) to install it -- you're out of luck.  The Ext2 FS drivers for MS Windows can't read Ext4 filesystems.

---

### Post by MintPaw on 2010-09-02
Darn ok then. I can access my windows drive from Linux so I think I'll just put stuff on that.

---

### Post by Mark Phelps on 2010-09-02
> **MintPaw said:**
> Darn ok then. I can access my windows drive from Linux so I think I'll just put stuff on that.

That's asking for trouble if you plan on writing to the drive.  One unclean shutdown and you won't be able to boot MS Windows anymore.

A better solution is to allocate a shared NTFS data partition. Since you won't be booting from it, if it encounters the unclean shutdown problem, it's then a simple solution to boot into MS Windows and run chkdsk on it.

---

