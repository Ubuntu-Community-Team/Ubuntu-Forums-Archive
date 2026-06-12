---
title: "Rsync backup my server"
date: 2010-07-20
forum: General Help
---

### Post by izaakrach on 2010-07-20
This should be a quick one. I'm trying to backup a single directory and it's subdirectories on my Lucid Server to a freenas box across my network. This is what I'm using to do that.. 
 
rsync -r -a -v -z * --delete freenas:DSIBackups
 
It almost works perfectly except for one problem. When a file is deleted at the source, this command doesn't seem to delete it on the receiving end. I assumed that the --delete would do that but aparently not. Can anyone think of a reason that this would happen? Thanks

---

### Post by rubylaser on 2010-07-21
You have your options in the wrong order, just re-write your rsync line like this...
```
rsync -avz --delete * freenas:DSIBackups
```

And so you know it's normally a better idea to explicitly write out the paths you're syncing, so you don't have a goof up and overwrite something on the other end. 
```
rsync -avz --delete /path/to/backup/ freenas:DSIBackups
```

Finally, you could put this into your crontab, and let the system run your backup for you automatically in the background.  Hope that helps.

---

