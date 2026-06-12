---
title: "Access HDD from Win 7"
date: 2010-03-13
forum: General Help
---

### Post by ephracis on 2010-03-13
Hi,

I decided to switch from Ubuntu to Win 7 on my laptop and since I had /home on it's own partition I just installed Win7 over Ubuntu.

Now I can't get Windows to access this harddrive. It seems that there's some stuff stuck in the journal so it won't mount correctly. I decided to install VirtualBox and figured I could install Ubuntu there and use it to fix the partition. But now I can't figure out how to "share" a physical partition use VirtualBox (I can choose to use a physical disk to install to, but I don't want that, and if I want to add a second harddrive I can just create a new virtual one, which I don't want to do either).

So, anyone have any tips on how to solve this? Or maybe someone knows how to fix an EXT3 disk in Windows 7?

Thanks for any help.

---

### Post by Slim Odds on 2010-03-13
Why don't you use the Ubuntu Live CD?

---

### Post by Mark Phelps on 2010-03-14
So, are you trying to access a Linux filesystem from Win7?

You can try installing Ext2fs to allow Win7 to read the Linux files.  But, if it's readlly Ext4, it most probably will NOT be able to read them.

More info in the link below:

[http://e2fsprogs.sourceforge.net/ext2.html]("http://e2fsprogs.sourceforge.net/ext2.html")

---

