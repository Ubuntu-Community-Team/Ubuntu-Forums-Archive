---
title: "Using 'find' for daily backups"
date: 2009-10-16
forum: General Help
---

### Post by oldmankit on 2009-10-16
Hi,

I hope this is the right forum.  I couldn't find one specifically for bash commands.

I want to do a daily backup of all files modified within the past 24 hours, and send it to a web server.  This is in addition to a weekly backup to an external hard drive.  

The first hurdle is finding the right files.  I've pieced this command together from various websites:

```
find ~/ -path ~/downloads -prune -o \( ! -regex '.*/\..*' \) -type f -mtime 0
```
[LIST]
[*]I want to exclude ~/downloads because they're not important enough to go into the daily backup.  Hence:  -path ~/downloads -prune -o
[*]I don't want to bother with any hidden files.  Hence:   \( ! -regex '.*/\..*' \)
[*]I only want it to output files (not directories).  Hence:  -type f
[*]I only want files from the last 24 hours.  Hence:  -mtime 0
[/LIST]
This is almost perfect.  However, in the list of found files, it finds the ~/downloads directory.  It successfully excludes any subfolders and files within that, but still outputs the directory name itself!

All of the other results are as desired.  Please help me tidy this command so that the ~/downloads directory isn't in the list of found files.

Thank you.

---

### Post by Baelus on 2009-10-16
Just a shot in the dark. Try changing -path to -name.

No, wait. That won't work. Nevermind.

---

### Post by justleen on 2009-10-16
Use rsync for this... Since this way you will copy over existing files too...

If you want to strip the dirname, i'd use a sed to get rid of it (assuming your doing something with the output of find)
find . -name whaterever | sed 's/\.\/downloads//'

---

### Post by falconindy on 2009-10-16
Use tar directly, instead of find. Find will give you bad results, as filenames with special characters (e.g. spaces) will be parsed incorrectly.

From `man tar`:
```
       --newer-mtime DATE
              only store files whose contents have changed after DATE
```

edit: Rsync is also an option. Probably a better one.

---

### Post by oldmankit on 2009-10-18
Can I use rsync to find only files modified within a certain time frame (e.g. 24 hours)?  I don't want to put everything onto my online storage space, as it's very limited (100mb).  The daily backups are only if something goes wrong during the week.  Weekly backups, my whole system goes onto external harddrive using rsync.

I couldn't find any options for this in rsync.  I haven't looked for tar, yet.

---

### Post by oldmankit on 2010-11-17
I forgot to write my solution.

I use rsync (the 'time machine' version) for my weekly backups, and dropbox for everything else.

---

