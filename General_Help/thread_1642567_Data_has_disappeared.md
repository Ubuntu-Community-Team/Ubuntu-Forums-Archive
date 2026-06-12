---
title: "Data has disappeared"
date: 2010-12-10
forum: General Help
---

### Post by Biddlesby on 2010-12-10
So I copied a large amount of files (70gb or so) off an external hard disk onto a FAT32 partition. They all appeared fine, but after a restart most of them have disappeared - i.e. not showing in Nautilus/terminal. 

In Windows 7 the drive is coming up completely empty (it is even not showing files that have been there a while). But in both Ubuntu and Windows the hard disk is reporting the correct amount of used space.

Using Ubuntu Lucid.

What on earth is wrong??! I can't even re-copy the files over again, because there is now no space on the drive.

Thanks for any help

---

### Post by coffeecat on 2010-12-10
I have no idea what has gone wrong, except that FAT32 is a pretty flakey filesystem. I would have suggested seeing if they've gone into a hidden Linux trash folder, but that would have shown up under Windows. But have a look anyway. Press ctrl-H in Ubuntu to reveal hidden files/folders and see if there are any .Trash* folders. The other thing to look in are the folders that are hidden in Windows but which appear in Ubuntu. $RECYCLE.BIN seems a good place to start.

Other than that, sorry. I don't know.

**Edit:** yes, one other thing to suggest. Since both Ubuntu and Windows are both reporting the space used up, try running chkdsk from Windows. That might recover them.

---

### Post by Biddlesby on 2010-12-10
Thanks for the ideas. Unfortunately, no .trash

Is there a better filesystem to use, one that Ubuntu and Windows can share?

---

### Post by coffeecat on 2010-12-10
I'd go for NTFS. NTFS read-write is fine in Ubuntu and you have Windows to repair it with chkdsk if it gets corrupted. It's a much more robust filesystem than FAT - it's journalled, unlike FAT - and has a larger filesize limit. The limit is only 4GB in FAT32.

I'd much rather use NTFS than install a 3rd-party Windows driver for a Linux fileystem. There is, I believe, a driver now for ext4, but the Windows ext* drivers have to use a kludge to cope with Linux permissions.

---

### Post by Biddlesby on 2010-12-10
By the way, chkdsk proudly says it has corrected errors, but the files are still missing in action:

> C:\Windows\system32>chkdsk D: /F
The type of the file system is FAT32.
Volume media created 10/09/2010 20:38
Volume Serial Number is 72C8-FBE6
Windows is verifying files and folders...
Removing trailing folder entries from \QUINCE
File and folder verification is complete.
Convert lost chains to files (Y/N)? y
49997520 KB in 169 recovered files.
Windows has made corrections to the file system.
  125,767,680 KB total disk space.
       29,008 KB in 1,380 hidden files.
       39,056 KB in 2,438 folders.
  107,761,344 KB in 7,718 files.
   17,938,256 KB are available.

       16,384 bytes in each allocation unit.
    7,860,480 total allocation units on disk.
    1,121,141 allocation units available on disk.

---

