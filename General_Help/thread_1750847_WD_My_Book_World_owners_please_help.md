---
title: "WD My Book World owners please help"
date: 2011-05-05
forum: General Help
---

### Post by krumpy on 2011-05-05
I'm having a problem using rsync with my WD My Book World.  I keep getting error msgs like below.  

rsync: chgrp "/media/netdrive/UbuntuBackup/matt/Documents/LinuxDocs/CurrentSys/RESULTS.txt" failed: Permission denied (13)

Has anyone else ran into this problem?  My rsync cmd is: 
rsync -arv  --delete-after.

For those of you that do have this drive what does your fstab entry look like?  I'm currently mounting the drive using:

192.XXX.X.XXX/public  /media/netdrive cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

I've done tons of searching and keep getting conflicting information.  Any help would be greatly appreciated.

---

