---
title: "rsync help"
date: 2011-09-26
forum: General Help
---

### Post by jbowen7 on 2011-09-26
Does anyone know of a way to avoid copying files with rsync if a parent folder is added:

Say we have:

[B]/Archives/file.reallybigfile
/Backup/[/B]

Then after ```
rsync -a /Archives/ /Backup/
``` we would have:
[B]/Archives/file.reallybigfile
/Backup/file.reallybigfile[/B]

Now say you ```
mkdir /Archives/newdir && mv /Archives/file* /Archives/newdir/. 
```

Then you:
```
rsync -a /Archives/ /Backup/
```

You'd end up with two copies of file.reallybigfile in /Backup

```
find /Backup
```:
[B]/Backup
/Backup/file.reallybigfile
/Backup/newdir/file.reallybigfile[/B]



Any suggestions on how to get rsync to mv the file instead of copying it?

Say file.reallybigfile was a 1TB file, it's not so fun to transfer across a network, but if it were just moved on the dest to it's new spot, then we could avoid heavy transfers.

---

### Post by papibe on 2011-09-26
> **jbowen7 said:**
> Say file.reallybigfile was a 1TB file, it's not so fun to transfer across a network, ...
I would recommend using the option --partial to move big files over the network. rsync will keep all that is being transfer. In case the the transfer is interrupted, rsync won't start from the begining but it will use the temp files to recover much faster.

If you want to track the progress of what is being transfer, the option --progress is more useful for big files than the regular -v.

(You can save space by using -P that equals --partial and --progress).

Now regarding your main concern.

There are a few options you can add to avoid the transfer, however the success varies (the internal rsync comparison method is limited and not very documented).

The option --fuzzy will try to do just what you are asking for: look for similar files (similar size, date and filename) so that the transfer can be avoided, or at least speed-ed up.

This is not a perfect solution since rsync looks for similar files just in the same directory, so if you moved the file to other directory, you are out of luck (maybe it would work if moved to a subdirectory?).

Please note that, although the --delete option suggested by zackwasa, will effectively remove the duplicates, it does not work well with the --fuzzy option. In order to the fuzzy option to work, use the option --delete-after option.

I hope this helps,
Regards.

---

