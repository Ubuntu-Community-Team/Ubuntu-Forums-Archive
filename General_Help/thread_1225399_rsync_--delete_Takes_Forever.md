---
title: "rsync --delete Takes Forever"
date: 2009-07-28
forum: General Help
---

### Post by Penguin Guy on 2009-07-28
```
rsync -acv --del / /media/backup/$HOSTNAME:\ Backup/ --exclude-from="/usr/local/bin/exclude-list"
```

When using the --delete parameter with rsync it sometimes takes a few minutes, this is because of files changing during the rsync. A solution to this problem would be to do the backup while the partition is mounted read-only.

---

### Post by Penguin Guy on 2009-08-16
Bump.

---

### Post by vamped on 2009-08-16
I hate to take a wild stab at this without knowing for sure the solution, but since no one else has responded:

Perhaps you could try one of the other delete options, such as:
```
--delete-after
--delete-excluded
```

Or perhaps try to narrow down possible reasons by doing things such as:
```
--max-delete=NUM
--dry-run
```

---

### Post by Penguin Guy on 2009-08-17
I tried some of those an they didn't help so I added the -v parameter to see what was going on. It seems that it *is* only copying the files that have changed but is just doing it really, really slowly for some files (30 secs to copy a 200 byte file). None of my CPUs are struggling either, they are all on about 10%-25%.

---

### Post by Penguin Guy on 2009-08-29
Bump.

---

