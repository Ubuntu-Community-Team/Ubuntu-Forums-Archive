---
title: "How to check or copy files on your dual boot"
date: 2010-04-26
forum: General Help
---

### Post by chrissy.millichamp on 2010-04-26
How to check or copy files on your dual boot Linux/Win 7 from Ubuntu Lucid Lynx?

---

### Post by carl4926 on 2010-04-27
> **chrissy.millichamp said:**
> How to check or copy files on your dual boot Linux/Win 7 from Ubuntu Lucid Lynx?
Come again.......:?

---

### Post by chrissy.millichamp on 2010-04-27
Let me repeat that. My question was, how do you check or copy files from your Windows 7 to your Ubuntu Lucid.

---

### Post by Mickser_52 on 2010-04-27
I have a dual boot xp and ubuntu. I created a new partition and use it to transfer files from windows to ubuntu. It works most of the time

---

### Post by rightmind on 2010-04-27
> **chrissy.millichamp said:**
> Let me repeat that. My question was, how do you check or copy files from your Windows 7 to your Ubuntu Lucid.

Hmmm, you should already be able to see the file system by going into Places>Computer>---your partition Windows is on----

---

### Post by carl4926 on 2010-04-27
You can't use win7 to copy files to Linux

But you can use Linux to copy files from win7 to Linux

Windows cannot read Linux file system and old Bill doesn't want it too either.

---

### Post by 2hot6ft2 on 2010-04-27
> **carl4926 said:**
> You can't use win7 to copy files to Linux

But you can use Linux to copy files from win7 to Linux

Windows cannot read Linux file system and old Bill doesn't want it too either.

I don't know about win 7 but these are for windows
> The following Ext2fs Utilities are available:

    * e2fsprogs, which consists of e2fsck, mke2fs, debugfs, dumpe2fs, tune2fs, and most of the other core ext2fs filesystem utilities.
    * dump, which will allow you to make backups of your ext2 filesystems. It uses a format which is compatible with the BSD dump and restore programs.
    * defrag, which will defragment your ext2 filesystem
    * ext2ed, which is a text/windows (curses) interface for examining and editing an ext2 filesystem. It unfortunately is limited to filesystems smaller than 2GB, and is heavily Intel byte order dependent, and has apparently been abandoned by its original author. (So for those people who were used to seeing ext2ed in older Linux distributions, and wondered where it went to, that's the explanation.)

      It has been integrated into e2fsprogs version 1.28, but its limitations mean that it should only be used by developers who need to generate test cases.
    * Ext2fsd, An ext2 filesystem driver for Windows NT/2K/XP. The most recent version has read-write support. 
[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

---

### Post by chrissy.millichamp on 2010-04-27
Sorry I think I havent been really clear here. How do you access from Ubuntu to your files in Windows 7?

---

### Post by towheedm on 2010-04-27
> **chrissy.millichamp said:**
> Sorry I think I havent been really clear here. How do you access from Ubuntu to your files in Windows 7?

OK to make it clear.  Open Nautilus (click on Applications => Accessories => Nautilus).  On the left pane, which is similar to Explorer's folders pane, you should see several drives (mount points).  One of these should be the name of the partition that Win7 was installed to, ie: Win7, Local Disk etc.  Now click on it.  You may be required to enter your password.  Once the password is accepted, it will open the drive and show the files on the right pane.  Simply copy and paste or drag and drop the files of interest.

Hope it helps.

---

### Post by jonny163 on 2010-04-30
I wondered about this too. The ntfs partition for Windows 7 should appear in Places. In my Places it is called '77 GB Filesystem'. You can copy and paste your files from there into the Ubuntu partition if you want. Just do it as normal, copy > paste into desired Ubuntu folder
I am trying to save space so I asked if there was a way to access the Windows 7 partition from Ubuntu without copying and pasting everything over.
Here is the thread [[URL="http://ubuntuforums.org/showthread.php?t=1464857"]**Dual  Boot: Accessing Windows Partition of HDD from Lucid]("http://ubuntuforums.org/showthread.php?t=1464857")**[/URL]
Hope this helps :D

---

### Post by cgroza on 2010-04-30
> **carl4926 said:**
> You can't use win7 to copy files to Linux

But you can use Linux to copy files from win7 to Linux

Windows cannot read Linux file system and old Bill doesn't want it too either.
You can but you have to install proper drivers...

---

