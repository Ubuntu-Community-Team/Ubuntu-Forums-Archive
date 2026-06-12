---
title: "Sbackup doesn't restore all files"
date: 2010-05-02
forum: General Help
---

### Post by lakelovers on 2010-05-02
I moved up to 10.4 which is working great. I backed up my files with Sbackup so now I'm trying to restore my Home folder but it appears that not all files are restored. I'm restoring from a "full" backup on an external drive. Dumb question: Do I need to restore all the directories (etc, home, usr, var) to get all my home folders/files restored? Or why don't all my Home foldersfiles show after restoring "Home"?

**Edit**Perhaps I have an answer. It appears that I have to install individual folders/files. I assumed that if I selected the Home folder that all sub folder and files would be restored. Apparently not. I have restored individual sub-folders but not parent plus child directories.

---

### Post by Zill on 2010-05-02
The SBackup Config "Backup Properties" window specifies which directories will be saved in the "Include" tab.  The "Exclude" tab specifies which paths and filetypes etc will *not* be saved.  By default, some files will be excluded, hence the failure to restore *all* files.  However, you can change the Included/Excluded tabs to suit your exact requirements.

If you look at the SBackup configuration file you can see at a glance which directories/filetypes will be included and excluded:
```
cat /etc/sbackup.conf
```

---

### Post by lakelovers on 2010-05-02
Thanks for the info. I'm working with it.

---

