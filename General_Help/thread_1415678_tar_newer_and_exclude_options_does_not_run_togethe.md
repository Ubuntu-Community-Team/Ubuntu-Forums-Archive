---
title: "tar newer and exclude options does not run together"
date: 2010-02-25
forum: General Help
---

### Post by parrimin on 2010-02-25
Hi,

Im trying to make backups using tar, and incremental backups using --newer. The scripts are:
```

tar -czvf $DISKPATH/backupRepos.tgz /home/repos/ --exclude /home/repos/Temp

```
for general backup (on saturdays)

and
```

tar -czvf --newer="`date -r $DISKPATH/backupRepos.tgz +%F`" $DISKPATH/backupRepos-inc.tgz /home/repos/ --exclude /home/repos/Temp/

```
for incremental the rest of the week.

The problem is that the first script runs OK, excluding /home/repos/Temp from the backup, but on the second, it makes incremental OK, but doesnt exclude Temp folder. 
Anybody knows how can i fix this script to continue making incremental but excluding also?

Thanks

---

### Post by nixclusive on 2010-02-25
> tar -czvf --newer="`date -r $DISKPATH/backupRepos.tgz +%F`" $DISKPATH/backupRepos-inc.tgz /home/repos/ --exclude /home/repos/Temp/

It should work if you remove the "/" after "Temp" in the above command:

```
tar -czvf --newer="`date -r $DISKPATH/backupRepos.tgz +%F`" $DISKPATH/backupRepos-inc.tgz /home/repos/ --exclude /home/repos/Temp
```

---

### Post by parrimin on 2010-02-25
> **nixclusive said:**
> It should work if you remove the "/" after "Temp" in the above command:

Uoooo, only that!!!!? Thank you very much!

---

