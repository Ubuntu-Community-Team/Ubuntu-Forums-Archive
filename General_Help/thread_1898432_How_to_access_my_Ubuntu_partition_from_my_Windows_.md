---
title: "How to access my Ubuntu partition from my Windows 7 partition?"
date: 2011-12-21
forum: General Help
---

### Post by Shavitborisov on 2011-12-21
Hello,
I just finished installing my operating systems - two general partitions for Windows 7 and Linux Ubuntu 10.04, and a few smaller partitions like Linux swap, ESP and some more.

Anyway, I'm a new user to Linux, and I noticed that I can access my Windows files from Ubuntu. But I didn't find anyway to access my Linux files from Windows and **actually be able to edit** them.

Does anyone know what to do?

Thanks :D

---

### Post by SaintDanBert on 2011-12-21
First, you must know the file system type that you want to access.
I expect you most likely have EXT4 or EXT3 or EXT2.  There are other types -- your mileage may vary.

If you google "ext3 windows" you will get several items -- one of which might meet your needs.  **Access** comes in a couple of categories:
[list]
[*]applications
[*]drivers
[/list]
In the first case, you get an application that looks very much like the win-dose file manager -- left panel folder tree with right panel contents. Click-drag-drop --> **access**.

In the latter case, your linux partitions get assigned a win-dose drive letter and you use the normal win-dose tools to **access**. These are few and far between since it is not that easy to create driver-class software in the win-dose world.

You might find this article a good place to start:
[Reading Ext3/Ext4 From Windows-7](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

I hope this helps,
~~~ 0;-Dan

---

### Post by oldfred on 2011-12-21
I believe the NTFS drive in Linux is better than any of the drivers for Windows to try to read Linux partitions. Much of the issue is ownership & permissions which Windows does not support and Linux files systems have to have.

I also do not recommend any writing into another system partition and therefore always separating systems from data. Many Windows users have also suggested a d: or data drive, so when you have to reinstall Windows to fix it you do not have to reinstall all your data (you must still back up your data).

I have used a shared NTFS (originally FAT) partition with XP since 2006 without issue. I have my Firefox & Thunderbird profiles in the shared NTFS partition.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by SaintDanBert on 2011-12-21
If I understand correctly, this sounds like the best of both worlds:
```

{Win Sys f/s}------- NTFS -----+
{Win Data f/s}------ NTFS -----+
...                            +----- WinXX read/write
{shared data f/s}--- NTFS ----------- both read/write
...                            +----- Linux read/write
{Lnx "root" f/s}---- EXT4 -----+
{Lnx /home fs}------ EXT4 -----+

```
And you base this on the opinion that Linux NTFS I/O is a better feature than any winXX implementation of EXTx.

This leaves open some other questions:
[list]
[*]is the shared data a $HOME folder?
[*]does linux $HOME have a file link into the shared space?
[*]does winXX use the shared space for "home" files and folders?
[*]do you tell winXX to relocate MyDocuments to the shared space?
[/list]

If these answers are YES, then where are details about how to implement all of these answers?

Thanks again,
~~~ 0;-Dan

---

### Post by oldfred on 2011-12-21
You do not need two NTFS partitions, but some have many as they put different data in different partitions. It becomes a trade off on size, use and potential filling of one partition and lots of room on the others and then having to reorganize. One disadvantage of one large partition is if you ever have corruption or accidentally erase data, recovery is easier from a smaller partition.

I think answers to all your other questions are in the links already posted. I did not move XP's My Documents as some have done as I tried to save everything into the shared NTFS data partition. But a few apps hide data in program folders, apps folders or other locations and do not give much choice on where. For those I jsut wrote a .bat file to regularly copy the data to the shared and backed up the shared partition.

I find linking folders from the shared into my Ubuntu /home works well, but if networking (Samba) it may not follow links.

Mozilla has info on how to shared. I just moved the entire profiles to my shared and changed profile.ini in both Windows & Ubuntu to look to the shared partition for Firefox & Thunderbird.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by SaintDanBert on 2011-12-22
> **oldfred said:**
> 
...
I think answers to all your other questions are in the links already posted. I did not move XP's My Documents as some have done as I tried to save everything into the shared NTFS data partition. But a few apps hide data in program folders, apps folders or other locations and do not give much choice on where. For those I jsut wrote a .bat file to regularly copy the data to the shared and backed up the shared partition.


I've loaded **Cygwin** on win-dose so that I have some real tools -- including bash and rsync. See [Cygwin tools for Windows](http://www.google.com/url?sa=t&rct=j&q=cygwin&source=web&cd=1&ved=0CDoQFjAA&url=http%3A%2F%2Fwww.cygwin.com%2F&ei=i2rzTuy4Buby2QXoxZ26Ag&usg=AFQjCNG181i4HT_pzwalR1pEs9gAFGqazQ&sig2=ryC9TbXxZJC2LkxlcRmAKg) That might be heavy weight for some.  

An alternative is to find win-dose editions of **rsync** and other GNU file management tools. See [GNU Tools for Windows](http://gnuwin32.sourceforge.net/)

Cheers,
~~~ 0;-Dan

---

