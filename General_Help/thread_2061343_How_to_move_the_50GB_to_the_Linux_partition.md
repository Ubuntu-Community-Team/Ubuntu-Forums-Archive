---
title: "How to move the 50GB to the Linux partition?"
date: 2012-09-22
forum: General Help
---

### Post by GJ1234 on 2012-09-22
Hello everybody,

I'd like to know how I can move the 50 GB of unallocated to the partition on which I have Ubuntu installed.
I have no idea why it won't just let me add.
Here is a screenshot.

Oh and btw yes I booted from usb

[IMG]http://i.imgur.com/3x27X.png[/IMG]

---

### Post by Cheesemill on 2012-09-22
You just need to do the steps in the correct order:

First of all make sure you have a backup as any sort of partitioning operations carry an element of risk.

1 - Right click on sda6 and select 'swapoff'.
2 - Resize sda4 all the way to the left so that the unallocated space is inside your extended partition.
3 - Resize sda5 to use the free space.

---

### Post by jerrrys on 2012-09-22
You think that pic is big enough?

[http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-resize-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-resize-partition)

---

### Post by oldfred on 2012-09-22
Please use the paperclip icon in the edit panel above your message to attach screenshots. They will be less overwhelming.

I am not a fan of large / (root) partitions. Your Windows also is not very full. 

I prefer to have data partition(s). If sharing with Windows you may have lots of data you want to use from both systems. I have Firefox & Thunderbird profiles & all photos for the Windows current version of Picasa in a shared NTFS partition. Then I am running the same applications in both systems and using the same data from the shared partition.

I still have shared NTFS, but have stopped using XP. Now all my new data is in a Linux formated partition that I shared with several installs of Ubuntu. 

If you use a shared NTFS, you then can set the Windows system partition or c: to be read only. That helps revent issues where the NTFS driver in Ubuntu exposes all the hidden files & folders that Windows normally hides to prevent accidents.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

---

