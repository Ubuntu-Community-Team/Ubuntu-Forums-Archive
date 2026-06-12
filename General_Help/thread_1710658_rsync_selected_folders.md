---
title: "rsync selected folders"
date: 2011-03-20
forum: General Help
---

### Post by jcoles on 2011-03-20
Using Grsync for backup of my home directory is a breeze. 

But, what if I want to back up only selected directories? I'm having trouble interpreting the rsync options/syntax required to do this.

The man page implies that it is possible to specify multiple source directories to be copied to the destination. Here is one of the examples they provide (about line 2932):

rsync -a --relative me/foo you/ /dest

But when I try it, the two sources are treated as one source:

rsync -a --relative source1 source2 /media/backup/

rsync: link_stat "/home/user/source1 source2" failed: No such file or directory (2)

Have I misinterpreted something? 

It looks like I'll need a separate Grsync session for each source directory.

---

### Post by gandaran on 2011-03-20
```
rsync -a --relative /home/user/source1 /home/user/source2 /media/backup/
```
this should work.

edit:
just read you post again and noticed this time you are using grsync, in fact grsync doesn't support multiple sources, but can only be done using the advanced options, sorry I don't know exactly what to put there.

---

### Post by Wharf Rat on 2011-03-20
> **jcoles said:**
> 

rsync -a --relative source1 source2 /media/backup/

.
You might try using a source file instead of multiple files on the command line.
Personally, I have yet to get ANY of the GUI front ends for rsync to work properly when going between machines.  They work fine as long as you want to copy your data to the same machine.
Thus, I  have had to revert to CLI.   

Command:
rsync -a --relative sourcefile.txt /media/backup/

Contents of source file:

# This is a list of directories I want to back up using rsync

home/photos/
home/documents/
# skip home/music/

---

