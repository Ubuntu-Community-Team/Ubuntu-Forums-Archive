---
title: "Recovering data from unmountable file system? (reiserfs)"
date: 2010-12-14
forum: General Help
---

### Post by MadJester on 2010-12-14
I recently had to replace the hard drive in my laptop.  I was attempting to upgrade from 9.04 to 10.04.  The upgrade kept failing with bizarre errors.  I eventually tracked them to a problem with the file system (reiserfs).  An attempt to repair the file system discovered hundreds of bad blocks.  I bought a new drive and setup a fresh install of 10.04.  However, the aborted file system repair (reiserfsck --rebuild-tree) left the file system in an unmountable state.  I could presumably use the -B (badblocks) option and keep adding a new block to the file each time it aborts, until I can through all bad blocks, but I am hoping there is a more expedient and sensible way to get old data off of the drive.

Suggestions or experience is appreciated.

---

### Post by jim_deadlock on 2010-12-14
This site has some great tools:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by MadJester on 2010-12-14
Those tools do not support reiserfs.  Any other suggestions?

---

### Post by MadJester on 2010-12-17
Still hoping for some insight.  Any one use any other tools that support reiserfs?

---

### Post by Rubi1200 on 2010-12-17
Hi,
I hope that this link will help you:
[http://www.linuxquestions.org/linux/answers/Hardware/ReiserFS_Data_Recovery_Tips](http://www.linuxquestions.org/linux/answers/Hardware/ReiserFS_Data_Recovery_Tips)

EDIT:
more links on the same subject:
[http://www.cgsecurity.org/wiki/ReiserFS_File_Undelete_HOWTO](http://www.cgsecurity.org/wiki/ReiserFS_File_Undelete_HOWTO)
[http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html)

---

### Post by Zill on 2010-12-17
MadJester:  This is probably not what you want to hear but I have never had much success with recovering damaged file systems.  ReiserFS is very robust but can still get corrupted, possibly by a hardware failure.

I suggest you just replace the damaged drive and then restore data from your latest backup - it will be far quicker in the long run IMHO.

---

### Post by MadJester on 2010-12-21
I used the tools from cgsecurity.org, but too much of the data was corrupted.  I am assuming this is because they don't work as well with reiserfs.  I am currently doing it the manual way, rebuilding the filesystem and excluding bad blocks.  I am hoping I will be able to get the filesystem to a mountable state and pull of any data I might like while I still can.

---

