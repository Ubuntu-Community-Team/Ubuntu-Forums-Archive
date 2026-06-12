---
title: "Comparing removable drives"
date: 2009-10-25
forum: General Help
---

### Post by Citizen Bleys on 2009-10-25
I'm looking for a Linux utility that will compare two removable drives and generate a list of files that are on only one of the drives.  I know the command-line app diff can do something like that for individual files, but does anyone know of something that can do it for entire volumes, mounted or no?

Here's the scenario.  Me and a buddy of mine each have 1 TB external hard drives.  Most of the content I have on my drive came from his originally, but his drive has some read/write errors.  What I want to do is come up with a list of files that are on his drive but not mine so that he can back up everything I don't have and format it.  It's not practical to copy everything over to my drive because I don't have enough room for my own backups *plus* his drive (his is full to brimming).

I'd prefer to do it all through the CLI without installing anything on my computer.

---

### Post by SPr on 2009-10-25
Perhaps this?
```

ls -R /media/disk>disk
ls -R /media/disk-1>disk-1
diff disk disk-1

```

Or check out rsync.

---

### Post by Citizen Bleys on 2009-10-25
Why the deuce didn't I think of that?

---

