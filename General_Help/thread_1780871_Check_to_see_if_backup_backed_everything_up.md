---
title: "Check to see if backup backed everything up"
date: 2011-06-12
forum: General Help
---

### Post by kafka201 on 2011-06-12
I'm looking to do a clean reformat/install of Ubuntu after years of screwing around inside Ubuntu and generally messing things up.  I've backed everything (entire home folder, including hidden program files) to an external hard drive and am nearly ready to format/install.  For the last step I'd like to make sure that pretty much everything was backed-up(there were a few useless files that I had to skip because of the difference between ext4 and FAT32), so how would I do this?

Is there a program I can run that can tell me the differences between two folders?  I know I can use mc to compare to folders, but I've got way to many files to go through and compare each and every thing.  Any other options?

Thanks

---

### Post by gdonwallace on 2011-06-12
without knowing what you used to backup its hard to say.  If you used dd or rsync, then there are options that can be attached to those programs that check file creation dates to see if they need to be backed up.  If this is the first backup of this directory and you used either of these programs, then it will make a complete copy of the target and copy it to the destination..by default.

What program did you use for the backup.

---

### Post by kafka201 on 2011-06-12
I just copied and pasted everything from my home folder over to the external hard drive

---

### Post by sammiev on 2011-06-12
I use [Clonezilla]("http://clonezilla.org/clonezilla-live.php") to backup all my stuff and you can also verify your backup. GL :) Clonezilla can be used to backup other OS as well or even your entire HD. :)

---

### Post by ajgreeny on 2011-06-12
If your external disk is large enough, make a separate partition on it as ext2.  That way, all your files will keep their permissions etc etc, and you will not see any of the error messages that appear on copying/backing up to a fat32 disk.  Then I suggest either **rsync**, or if you want a GUI use **grsync**.

---

### Post by gdonwallace on 2011-06-13
If you copy and pasted, it is possible that you could have missed some hidden files and directories.  Its best to use some backup software, or use rsync or like the above post if the external hard drive is large enough use clonezilla to backup your directory.

---

