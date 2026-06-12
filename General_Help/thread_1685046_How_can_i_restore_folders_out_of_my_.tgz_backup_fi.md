---
title: "How can i restore folders out of my .tgz backup file?"
date: 2011-02-10
forum: General Help
---

### Post by latestbeats on 2011-02-10
Hi,
 
I'm using ubuntu for a few weeks now and i created a backup script that can copy some folders into a .tgz file. Now i want to place back the folders to where they come from and overwrite the original folder. like the /home folder in the .tgz file overwrite the /home folder on my harddrive. I already tried to do this with: tar xvpfz filename.tgz. But after that the folders came in the same folders as the backupfile stands.
 
How can i do this the right way?

---

### Post by Brandon Williams on 2011-02-10
Either run tar from the directory where you want the archived files to be placed, which would require you to specify the full path the .tgz file, or add "-C /desired/directory" to the tar command line, which tells tar to change to the /desired/directory before extracting the archive.

---

