---
title: "Ubuntu is not seeing the partition it is installed on???"
date: 2010-12-17
forum: General Help
---

### Post by Bobazonski on 2010-12-17
My machine has Windows 7 on it, which I have been using up until yesterday. I have two hard disks, one is a 250GB with one partition (Windows installed on it) and the other is a 1TB with four partitions.

One of the partitions of the larger drive has all of my media on it. It is also the partition I chose to install Ubuntu on (I used Wubi to install).

For some reason, in Ubuntu, when I go to "Computer," it will show the 250GB drive, and the OTHER three partitions of the 1TB drive, as well as "File System" (which is located on the partition not shown, but I can't move up to parent folder and see the other contents of the partition).

Why can't I see it? How can I fix it? I really want to watch a few videos while I'm using Ubuntu.

EDIT: The partition it isn't seeing is formatted the same exact way as the ones it can see--NTFS with 4KB clusters.

---

### Post by Bobazonski on 2010-12-17
There is one folder in "file system" named "root" and when I try to click on it, it says I don't have permission. I also can't enable permission in "properties" because "I am not the owner." Is this because Windows is somehow preventing me from using it?

Sorry if I'm asking some really noob questions here... I'm really new to Linux and having two operating systems on the same machine is kind of boggling...

---

### Post by bcbc on 2010-12-17
the host partition (the one you installed Ubuntu to) is mounted under /host 
You can access it from Computer, File system, /host
or just ALT-F2, nautilus /host
Create a bookmark for later use.

PS. don't update packages grub-pc and grub-common when using Wubi. They show up under "Recommended" updates in Update manager. If you do (in your particular install setup), it will prompt you whether you want to install grub (the bootloader) - in which case, you do not want to install it anywhere (or else you can override your windows bootloader). But best just not to update grub-*.

---

