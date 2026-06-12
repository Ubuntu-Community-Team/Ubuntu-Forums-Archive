---
title: "XFS /JFS External log"
date: 2011-09-25
forum: General Help
---

### Post by Nuvielle on 2011-09-25
Hello,

i have to say i am pretty happy with XFS and JFS as File system, after some little modifications it feels faster than the same system with ext4/3.

But i have a question for the Ability from JFS / XFS to write the log to an other Disk.

There are many Howto's for doing this, but no Howto i found says something about the targeted Partition. Has that Partition i want to log on a other target the same Filesystem as the FS i who gets that separate log ? is that a separate File wich gets written there or is that function using the target FS itself ?

Lovely Greets

---

### Post by Nuvielle on 2011-09-25
and i have a second question, are changes with hdparm disappearing after a restart ? If yes, how can i make them not disappering ?

---

### Post by Nuvielle on 2011-09-25
for example this 2 commands


mkfs.jfs -q -j ${LOGDEV} ${PRIMARY}



mkfs.xfs -f -l logdev=${LOGDEV},size=256m,lazy-count=1 
-d agcount=15 ${PRIMARY}

must logdev have the same FS as the primary ?  :sad:

---

