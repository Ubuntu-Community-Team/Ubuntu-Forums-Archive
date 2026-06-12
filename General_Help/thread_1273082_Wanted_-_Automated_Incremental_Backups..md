---
title: "Wanted - Automated Incremental Backups."
date: 2009-09-23
forum: General Help
---

### Post by Roasted on 2009-09-23
I use rsync with a script I wrote, but it just simply copies the data to my other drive.

I'm trying to track down a good way to take a "snapshot" and zip the data up into a package and save it to the remote directory. That way I can set it up to do daily backups and save 3-4 days on the spare drive.

How can I do this? I've tried GAdmin, Grsync, etc. But these options either didn't give me a scheduling feature or the incremental backup feature.

Any input?

---

### Post by FunkyRes on 2009-09-23
You can use cron to do it automatically.

---

### Post by Roasted on 2009-09-23
Right. And I use cron with rsync to do it automatically.

I guess what I want is to have the data packaged... so I can have a package from thursday, a package from friday, etc. Then if saturday I realize I have a corrupt file, I can pull the friday backup and dump it where I need to so I'm back in business.

---

### Post by A_Fiachra on 2009-09-23
I've used find | tar, it may seem clunky, but it works.

e.g.


```


find . -mmin -120 -type f | xargs tar -rvf ../`date +%a-%m-%d-%Y`.tar && bzip2 ../`date +%a-%m-%d-%Y`.tar


```

Naturally you want to adjust the mtime argument and the directories.

There is a trick with find:

```

find . -mtime 0 -exec ls -l {} \;

``` 

will print everything under the current directory that has been modified in the past 24 hours.

Obviously, if you want to tar up everything under / and store it on the same fs, you'll need to prune your find.

---

### Post by mike555 on 2009-09-23
sounds like what you want is "back in time " , from;  [http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by StuartN on 2009-09-23
You could combine **rsync** with **cp -al** (create hard-link copies) in a script to create virtual full backups, like this [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

