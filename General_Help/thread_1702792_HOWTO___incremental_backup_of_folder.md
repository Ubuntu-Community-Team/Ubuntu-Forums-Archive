---
title: "HOWTO:   incremental backup of folder ?"
date: 2011-03-08
forum: General Help
---

### Post by kapetr on 2011-03-08
Hello,

I have read something about backup, but I still can't find what I want:

**incremental backup of folder**

The problem with e.g. find&tar is, that I want backup not only files with modification time after x:y , but also older files, that have been copied into this folder after last backup.

Can someone help me how to do it ? 

Preferably with standard command line utils.


--kapetr

---

### Post by aeiah on 2011-03-08
i do this sorta thing, in a script:

first take a copy of the directory and put it on another drive (where the backups will reside). we'll call this ~/backup/one

next time you want to do a backup, copy the original backup to a new folder with hard links. this takes up no disk space:
```
cp -al ~/backup/one ~/backup/two
```

now, if we do an rsync from our source data to ~/backup/two it will only copy the bits that have changed.. the rest will stay hard-linked to the first backup. 
```

rsync -avH --delete ~/source ~/backup/two/
```

so the disk space used is only as much as the original copy + anything that's changed, but when you look at it you see all the old data too, because of hard links.


is this what you want? the problem is that the hard links will break if you archive the directories. you wont loose any data, but if you compress ~/backup/one and the original, the unchanged hardlinked files in ~/backup/two will become unlinked and you won't save much space.

---

### Post by kapetr on 2011-03-08
**rsync** ... that's it!

_Thank You._

I run now **rsync -vaxb --backup-dir .rsync.bak --suffix=$(date "+.%F_%T") fromdir todir**

that way I have real incremental backup :-)

Without the --suffix=$(date "+.%F_%T") only one backup of file is available (only one previous version).
But then I can't use --delete - it would delete other then actual suffixed files.

About the "links" i will learn more - just now is it all new for me.

BTW - why to use "cp -a" first ? Rsync itself do the job for me at first time run.

One more thanks.

--kapetr            [sorry please my English]

---

### Post by vanadium on 2011-03-08
The cp -a indeed is not needed. Moreover, the method described by aeiah is not the method to make snapshots, i.e., make a more current backup by hardlinking to files from a previous backup that have not changed. That would require the --link-dest option.

---

### Post by aeiah on 2011-03-09
cp -al links files instead of copying, and archives

rsync -H preserves hard links.


this is the same as using --link-dest=DIR in rsync. its an old habit and i often forget --link-dest exists in rsync. it didnt always, and old guides always talk about hard linking with cp -al instead since its guaranteed to work on any nix system no matter the version of rsync

---

### Post by vanadium on 2011-03-09
That is not quite right. -H will check for hardlinks and recreate these in the destination. Without the -H link, hardlinks in the source become separate files in the destination. The -H option takes considerably more time.

The --link-dest option is something else. It is in fact incorporating into the rsync command what you are doing "the old way". You use cp -al to create a hardlinked copy of ~/backup/one. This indeed goes very fast and does not take space. Then you update ~/backup/two with rsync.

The --link-dest allows you to do such a thing directly with rsync. 
```

rsync -av --delete --link-dest=~/backup/one <source> ~/backup/two

```
will rsync your <source> to ~/backup/two. However, for any file that exists in the source and that is identical in ~/backup/one, a hardlink will be created in ~/backup/two.

So this kind of combines your two steps into one command.

This approach is useful to create snapshot backups.

---

### Post by kapetr on 2011-03-15
Thanks for explaining that about hardlinks. It is sure more elegant then making copy and waste disk space.

Just one more question - is it possible to achieve that **--backup-dir bakdir** will create the "bakdir" outside of "destdir" ?

It would let me the possibility of using **--delete** together with multiple incremental backups.

Thanks  
--kapetr

---

