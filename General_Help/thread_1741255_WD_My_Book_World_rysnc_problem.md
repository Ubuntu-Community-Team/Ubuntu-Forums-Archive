---
title: "WD My Book World rysnc problem"
date: 2011-04-27
forum: General Help
---

### Post by krumpy on 2011-04-27
I'm having a problem using rsync with my WD My Book World.  I keep getting error msgs like below.  

rsync: chgrp "/media/netdrive/UbuntuBackup/matt/Documents/LinuxDocs/CurrentSys/RESULTS.txt" failed: Permission denied (13)

Google searches seem to indicate that the file system on the WD doesn't support the same permissioning as Linux and therefore changing certain parameters doesn't make sense.  Can I just reformat the drive?  On WD's website they said the drive is formated in a propriety format??  

Has anyone else ran into this problem.  I'm not so worried about maintaining the permissions exactly as they are on my system.  I mainly just want to backup everything.  My rsync cmd is just rsync -arv -delete-after.

---

### Post by krumpy on 2011-04-29
Anyone?

---

