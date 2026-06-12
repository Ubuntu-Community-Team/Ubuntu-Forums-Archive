---
title: "fsck on reiserfs"
date: 2006-05-05
forum: General Help
---

### Post by wizzkid on 2006-05-05
I installed my kubuntu using reiserfs filesystem. sudo touch /forcefsck doesnt work... is fsck is compatible with reiserfs?

Thanks.

---

### Post by Sef on 2006-05-05
What message do you get?

---

### Post by uteck on 2006-05-05
You may need specify fsck.reiserfs

---

### Post by wizzkid on 2006-05-22
I tried 
kdesu touch /forcefsck.reiserfs
kdesu touch /forcefsckreiserfs

but doesnt work on me. :-(

any clue on this?

Thanks

---

### Post by asimon on 2006-05-22
[QUOTE=wizzkid]I tried 
kdesu touch /forcefsck.reiserfs
kdesu touch /forcefsckreiserfs

but doesnt work on me. :-(

any clue on this?

Thanks[/QUOTE]
The existence of /forcefsck is tested in /etc/init.d/checkfs.sh and in /etc/init.d/checkroot.sh. If /forcefsck exists the fsck is called with the "-f" option. For fsck.ext3 this does a forced check, even if the filesystem seems clear. But this doesn't work for reiserfs. From the fsck.reiserfs man page:
```
-r, -f These options are not yet operational and therefore are ignored.
```

Thus the existence of /forcefsck has no meaning for reiserfs filesystems as reiserfs has no forced checks (just as xfs AFAIK).

---

### Post by wizzkid on 2006-05-23
Thanks Asimon.

Which FS you refer? :) thanks.

---

