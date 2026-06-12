---
title: "Automatic revisioned backup/sync"
date: 2010-09-10
forum: General Help
---

### Post by DeepThoughts on 2010-09-10
I wonder if anyone knows of a cross platform sync/backup utility that can do the following:

[LIST]
[*]Incremental backups
[*]Revisioned backup (possibility to not just restore the latest but to go back to a specific point in time)
[*]Two way sync. E.g. two computers sync to the same server and the server also pushes changes to the clients (well I suppose it might be possible to solve it by restoring the latest backup also)
[*]Cross platform: Linux, Windows & Mac (the server side may be Linux only)
[/LIST]

Basically I want a revisioned version of Unison or a local version of Dropbox with support for custom folders. Depending on how you see it.

I'm not afraid to script things together if no pre-built solution exists but there are tools that when combined might do this. However it must be possible to automate, this comes from the fact that I want to be able to schedule it so it performs automatically. (If there is a way to push changes to the computers, like Dropbox, that's a plus but not a requirement.) This also means that a command line utility might be preferable over a GUI-only one.

So, any tips? If you know of something that almost fits but not quite, please don't be afraid to post it anyways. Anything that gets me close is appreciated.

---

### Post by velmont on 2010-10-08
Unison plus rsnapshot (built on rsync).

Unison for the sync-part, and the keeping everything nicely updated. You should use **incron** or just normal cron to make it automatic.

Then, on the server, you can use rsnapshot to make incremental backups.

Also worth to mention; I don't use rsnapshot for my own files like this. Unison has a setting backups= that you can set to e.g. 3, then it will keep 3 older files when it modifies another one. This is good enough for me, so if I delete a file, and everything is synced, I can still find that file, along with 2 older versions of that file in .unison/backup/.

---

