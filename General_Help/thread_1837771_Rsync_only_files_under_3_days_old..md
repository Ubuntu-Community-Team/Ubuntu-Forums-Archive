---
title: "Rsync only files under 3 days old."
date: 2011-09-02
forum: General Help
---

### Post by MrWestwood on 2011-09-02
Hi there.

I have an Rsync set up between two images and the data in the source location goes back 45 days. I'm wanting rsync to only fetch the data that is less than 5 days old. Is this possible? I have the Rsync manual but can's seem to find anything. 

Would it be possible to use find over ssh and append rsync to whatever that outputs?

---

### Post by papibe on 2011-09-03
```
$ cd source
$ find . -mtime +3 -type f -print0 | rsync -0v --files-from=- ~/source ~/destination

```
find:
[INDENT]-mtime +3 will match files 3 days old, and older.
-type f will find only files.
-print0 will print results with a null at the end, safer in case of strange characters in the filenames.[/INDENT]

rsync:
[INDENT]-0 uses null as a separation.
-v verbose, to see what's going on.
--files-from=- receive file list from the standard input.[/INDENT]

Note: since the list of files has to be relative to the source directory, I 'cd' to the source directory first. As a side effect you'll need to use absolute paths as a source and destination (remember that ~ will expand to /home/youruser).

I hope it helps,
Regards.

---

### Post by MrWestwood on 2011-09-05
That looks pretty bang on, thanks.

I was thinking over the weekend of a better way to do it and originally I was rsynching from destination wheras I did have the brain wave that rsynching from source would do the job. You have verified that for me.

Many thanks.

---

