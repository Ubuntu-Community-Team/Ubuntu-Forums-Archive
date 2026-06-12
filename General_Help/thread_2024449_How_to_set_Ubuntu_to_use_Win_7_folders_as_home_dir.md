---
title: "How to set Ubuntu to use Win 7 folders as home directories"
date: 2012-07-13
forum: General Help
---

### Post by polaatx on 2012-07-13
Hello, 

I have been forced to install win7 on a different partition on my laptop because of particular software I need that is only availalbe for windows. 

My question is whether possible to tell Ubuntu 10.04 to use win7 folders for saving documents, videos, pictures, downloads. 

[This article]("http://silverwav.wordpress.com/2010/03/21/note-ubuntu-default-folders/") shows how to change default folder *inside* Ubuntu's home folder. My question is whether possible to set default folders *outside* Ubuntu's partition, or another drive entirely.

I am not proficient. Please kindly give me the exact code if I have to use the terminal. I have had a difficult time navigating to and in other driver using the terminal when it came up in the past.

---

### Post by 3Miro on 2012-07-13
You cannot set the home folder itself, but you can set the sub-folders. You can use fstab to make sure the windows partition is always mounted automatically and then use symlink. I would say this is the easiest way.

Here is the official Ubuntu tutorial for fstab:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Here is something symlink:
[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

The basic idea is:
```
ln -s /media/Window_Partition/path/to/Documents /home/your_user_name/Documents
```
You will have to empty the Documents folder and delete it first.

Note that saving important files to NTFS is not recommended for security and stability reasons. Personally, I will not trust my important documents to Linux to write on Windows partition. It is OK to move a file form Linux to Windows, then you still have the Linux copy if things break, but using windows partition all the time is not recommended.

---

### Post by BBQdave on 2012-07-13
> **polaatx said:**
> My question is whether possible to tell Ubuntu 10.04 to use win7 folders for saving documents, videos, pictures, downloads.

Linux and Windows uses two different file systems. You can write files to *fat 16* or *fat 32* from Linux and then access those files with a common application.

An example would be a computer with Ubuntu and LibreOffice, you create a document (with LibreOffice) and save it to a thumb drive formatted to *fat 32*. On another computer with Windows 7 and LibreOffice, you could read the file (LibreOffice) from the thumb drive (*fat 32*), and edit it and save it.

As far as on the same computer (two different OS's), I am not sure what it would gain you, because the file systems (and most applications) are different and would not recognise each other. You could create a separate partition (*fat 32*) that the two different OS's (Linux and Windows) could access (share files and folders). But again, there are only a few applications that work in both Linux and Windows (like LibreOffice). So I am not sure how much you could share between Linux and Windows.

---

### Post by oldfred on 2012-07-13
I use a shared NTFS for some data I used to shared with XP and another in Linux format for most new data. Both have symlinked folders into my /home. I have used the shared NTFS (was FAT32 originally) since 2006.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

