---
title: "29 GB which I can't see"
date: 2009-08-03
forum: General Help
---

### Post by chmacka on 2009-08-03
I formated my new 500 GB external hard disk to ext3 filesystem. After formatting, properties window is showing that 23,5 GB of space is used. The only folder in there is lost+found which I can only access as root. I'm guessing that lost+found is taking up 23,5 GB.

I found out what lost+found folder is: [http://ubuntuforums.org/showpost.php?p=5419736&postcount=4](http://ubuntuforums.org/showpost.php?p=5419736&postcount=4)

But could it be taking 23 GB after format? Can I still delete it?

---

### Post by insane_alien on 2009-08-03
lost and found is just an empty folder. it will only contain files when fsck fails.

the 29GB is space reserved for metadata on the drive stuff like the journal and inode's. these take up some space.

---

### Post by chmacka on 2009-08-03
Thanks! Before I saw your answer I found this topic: [http://ubuntuforums.org/showthread.php?t=1047370](http://ubuntuforums.org/showthread.php?t=1047370)

Thanks for the quick response!

---

