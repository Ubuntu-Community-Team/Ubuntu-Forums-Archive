---
title: "Sharing files between Windows and Ubuntu"
date: 2010-11-09
forum: General Help
---

### Post by Enigmapond on 2010-11-09
I have a rather simple question...at least I hope. I run a dual boot of Win7 64bit and Lucid 32bit. Whilst using Ubuntu, (the majority of the time) I can access my whole Windoze side and see all the files. When I'm using Windoze, it doesn't even recognize that I have this Linux partition. Is there a way that I can access the files on Ubuntu from Windoze? Right now I have to keep most of the files on the Windoze partition so this can be done. Your help would be greatly appreciated.

---

### Post by ki4jgt on 2010-11-09
If you know anything about partitioning, create a partition which is big enough to house your files. Personally, I wouldn't want Windows to see my Ubuntu install b/c of the fear that a windows virus could damage my stuff.

---

### Post by grepcat on 2010-11-09
You might try Ext2Read - [http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

I used to use tools of this kind (but never this one) for reading my Linux partitions, before deciding that Windows was too much of a pane in the glass.

---

### Post by Enigmapond on 2010-11-09
Thank you both for the quick response. Yea I figured it was going to be something like that but I was trying to NOT do another partition I'll download that app and see how it works. I truly wish I could just give up the Windoze entirely..more than anything but I do a lot of music production and unfortunately need it. Thanks very much though..trying Ext2Read.

Cheers!

---

### Post by SaintDanBert on 2010-11-09
While certainly not optimal, you could create a Fat32 (vfat) partition that was visible to both dual-boot personalities. There are lots of reasons why fat32 file systems are problematic, but at least they are read-write for win-doze and linux alike.

Another much more complex option involves using VirtualBox or similar and "virtualize" one of your personalities.

Bonne chance,
~~~ 0;-Dan

---

### Post by ki4jgt on 2010-11-09
> **SaintDanBert said:**
> While certainly not optimal, you could create a Fat32 (vfat) partition that was visible to both dual-boot personalities. There are lots of reasons why fat32 file systems are problematic, but at least they are read-write for win-doze and linux alike.

Another much more complex option involves using VirtualBox or similar and "virtualize" one of your personalities.

Bonne chance,
~~~ 0;-Dan

The second option would be kind of awesome. I need to try that sometime.

---

### Post by oldfred on 2010-11-09
I do not like to have a foreign system write into another system's partition. I read from my XP partition but do not write into it except for repairs. 

Also many windows users recommend that you have a separate data partition with windows, so when you have to reinstall windows your data does not have to be reinstalled.

I used a FAT partition as my shared partition with XP for several years but then realized that some larger files over 4GB were corrupted. I converted to NTFS, but you still need to run chkdsk on the NTFS partition occasionally. 

I still have my NTFS shared partition, but am in windows so little that most of my data is in a /data partition that I use instead of a separate /home for all my other data.

---

### Post by Enigmapond on 2010-11-09
> **grepcat said:**
> You might try Ext2Read - [http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

I used to use tools of this kind (but never this one) for reading my Linux partitions, before deciding that Windows was too much of a pane in the glass.

Thank you for this little programme! It works just wonderfully!!!

Cheers!

---

### Post by SaintDanBert on 2010-11-10
> **ki4jgt said:**
> The second option would be kind of awesome. I need to try that sometime.

Got my KI4 call in Roswell, GA 1979.
73 OM  de  KI4MQ
QTH Austin TX

... and phone texters thought they had a corner
on cryptic...

---

