---
title: "Format drive with data to two partions with different file systems."
date: 2010-08-01
forum: General Help
---

### Post by Hmmster on 2010-08-01
Hey!
Okay, so here's what i want to do.
I have a harddrive with Ubuntu 10.04 on it, the biggest partition is a 242gb ext3 partition.
I want to format a part of that to FAT, without loosing any data from the hard drive.
Is this possible?

---

### Post by drs305 on 2010-08-01
Sure.

If you only have an Ubuntu partition, or want to take space from your Ubuntu partition, it must be unmounted. 

To accomplish your task, first backup any important data files if you have space elsewhere.

Start the Ubuntu LiveCD, boot to the Desktop, and open Gparted (System, Administration, Gparted). You will have to unmount "swap" if it is mounted, and make sure your Ubuntu partition is not mounted. Mounted partitions have a "key" icon next to them in the lower panel. You unmount them by selecting the partition, then from the top menu, Partition, Unmount (or Partition, Swapoff for the swap partition).

Refer to the second half of the first post in this thread for techniques on how to accomplish the task. The post was written for expanding the / partition, but the same principals apply for shrinking it:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by Hmmster on 2010-08-01
Thank you very much for the fast answer! :)

---

### Post by oldfred on 2010-08-01
Why FAT?

NTFS is better and works with both Ubuntu & windows. I only use FAT on small partitions or devices that require it like cameras flash cards.

NTFS and Fat info:
FAT 4GB max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by jerenept on 2010-08-01
You can resize it, and format the free space to FAT32 (recommended over FAT)

An Ubuntu live CD is probably a good choice to use. When it starts up, you just select "Try Ubuntu 10.04 without any change to your computer" or something to that effect. The when you get to the desktop, open System>Administration>Partition Editor
[COLOR="Red"]GParted is a powerful tool, capable of destroying data in an instant! Be careful.[/COLOR]

Now that you have read my cheerful warning, please right click the partition you wish to resize, and select "Resize/Move"

Resize it to the size you want it. Now, right click on the unallocated space. click "New". another window will open

Select "Fat32" in "File System" and set an (optional) partition label. Now click "Add".

the window will close, and now you click the tick at the top of the window. A window will come up with a warning, if you want to proceed, just click "Apply"

this operation will take a while. 

By the way, why do you need a FAT32 Partition?

---

