---
title: "Need a Linux Ext3 - Windows 7 NTFS file manager"
date: 2012-07-07
forum: General Help
---

### Post by OooBuntuRox on 2012-07-07
Hello,

I am trying to find a file manager for Windows7 that will allow me to both READ and WRITE to linux partitions. Particularly Ext3.

There are a few managers that say you can read linux partitions from windows and copy files. But it does not mention if you can WRITE to the same partitions. I rather not have to install and play, then uninstall just to find out.

Does anyone know?

Here are some I found by googling: 

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

[B]1: Explore2fs   
[/B]

[B]2: DiskInternals Linux Reader  
[/B]

**3: Ext2 Installable File System For Windows**



Thanks. OooBuntuRox, :guitar:

---

### Post by Cheesemill on 2012-07-07
[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

---

### Post by oldfred on 2012-07-08
I suggest a shared NTFS partition for any data you may want in both. 

I do not recommend writing into the system partition (reading is ok) except when you have to repair Windows from Linux. :) And the same from Windows into LInux although the drivers seem to work less well. Windows does not understand Linux permissions & ownership which can cause issues trying to write into a Linux partition.

Windows for whatever reason does not like too many writes from Ubuntu. May be because the Linux NTFS driver shows all files and lets you accidentally damage system or write into a hibernated system causing major issues. Best just to set system partition ( c: ) as read only. 

I have Firefox & Thunderbird profiles in a shared NTFS partition since XP and 6.06 without any real issues. I also have all photos and use the Windows version of Picasa in Ubuntu (wine).

---

