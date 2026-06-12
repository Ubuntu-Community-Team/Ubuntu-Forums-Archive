---
title: "Shift /home to another partition"
date: 2010-10-05
forum: General Help
---

### Post by sid.mallya on 2010-10-05
I didnt mount my /home in a separate partition during the installation process because I thought formatting the partition was a prerequisite to this. Obviously, I was wrong.

Anyway, I want to move my "/home" directory to another partition so if at all this OS gets corrupt for some reason, I dont have to worry about my data backup. Also I hear that "/home" directory can be shared on multiple OSes ? 

How do I do both of these things ?

:KS

---

### Post by Merthod on 2010-10-05
That task requires some advanced abilities. 

This may be useful for you:
[URL="http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/"]
http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/[/URL]

---

### Post by oldfred on 2010-10-05
You do not share /home with multiple OSes. You can use the same /home as you upgrade Ubuntu.

If you want to share across OSes, you need to create a /data partition and move most or all of your data out of /home into /data. 

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

