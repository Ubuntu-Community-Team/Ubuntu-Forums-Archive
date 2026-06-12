---
title: "ntldr is missing (Dual Boot Windows XP &amp; Xubuntu 10.04)"
date: 2011-04-12
forum: General Help
---

### Post by badpunk on 2011-04-12
Hello all,

I've been searching the forums but have yet to find a solution for my problem.

I recently installed Xubuntu 10.04 normally onto a partition on my harddisk, and was still also able to boot into windows xp without any problem. After many weeks of using xubuntu, I wanted to boot into windows xp today but i get a "ntldr is missing; press any button to restart".

I tried mounting the windows partition in xubuntu but all the files in that partition has a "locked" icon and are all gibberish. Previously, i could access the files on the windows partition but after trying to boot into xp today, i can't. Furthermore, I do not have the windows xp cd. 

I'm quite new to linux and i really hope that someone could help me out :D

---

### Post by dragonfly41 on 2011-04-12
This explains the error message ..

[http://support.microsoft.com/kb/318728](http://support.microsoft.com/kb/318728)

---

### Post by spielball on 2011-04-12
You could try Hiren's Boot CD and then run various tools to check the Windows partition, e.g. Checkdisk (chkdsk.exe), and recover files.
[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)[URL="http://www.hirensbootcd.org/download/"]
[/URL]

---

### Post by Mark Phelps on 2011-04-12
> **badpunk said:**
> ... and are all gibberish. Previously, i could access the files on the windows partition but after trying to boot into xp today, i can't.

You should be able to see the contents of many of the file without problems -- but not the executables.  If you're looking at text files and they are still gibberish, it's most likely your Windows filesystem got corrupted.

In that case, you will need to download and burn the Hiren's Boot CD, boot from it, and use the hard disk utilities to try to repair the filesystem.

---

### Post by badpunk on 2011-04-15
> **Mark Phelps said:**
> You should be able to see the contents of many of the file without problems -- but not the executables.  If you're looking at text files and they are still gibberish, it's most likely your Windows filesystem got corrupted.

In that case, you will need to download and burn the Hiren's Boot CD, boot from it, and use the hard disk utilities to try to repair the filesystem.

Hello, thanks for the reply. Which programs should I use in the hiren CD? I tried check disk, but it doesn't even detect the partition that XP is installed on.

Edit: i managed to mount the drive that contains XP, but when i use check disk, it says that the type of file system is RAW, and cannot be checked.

---

