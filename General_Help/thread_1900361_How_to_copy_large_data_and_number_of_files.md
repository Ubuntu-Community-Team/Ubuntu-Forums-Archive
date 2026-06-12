---
title: "How to copy large data and number of files"
date: 2011-12-26
forum: General Help
---

### Post by deepakdeshp on 2011-12-26
I want to to backup my external drive and it is 250gb data divided nto a very large no. of files , more than 2,00,000 files.

AT the same time, I should be able to search the backup for any file and should be able to extract any of them.
# cp -r dir1 dir2 may not be an efficient solution to take the backup.

Any suggestions?

---

### Post by vanadium on 2011-12-26
rsync -av <sourcedir> <destinationdir>

will copy it all, preserving atributes, permissions, etc. The copy is incremental. It will only copy files that are not in the destination or have changed. As such, it is ideal for backup purposes.

Add the option --delete to have files removed in the destination that are not anymore there in the source (be careful that you properly specify source and destination!).

---

### Post by The Cog on 2011-12-26
+1
rsync is fantastic for that sort of thing. There is a GUI front end for rsync called grsync if you prefer a GUI.

---

### Post by deepakdeshp on 2012-01-13
I prefer the command line. Thanks for the suggestion. I am still to implement it though

---

