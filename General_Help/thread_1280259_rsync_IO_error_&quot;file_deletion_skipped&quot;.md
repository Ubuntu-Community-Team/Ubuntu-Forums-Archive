---
title: "rsync IO error: &quot;file deletion skipped&quot;"
date: 2009-10-01
forum: General Help
---

### Post by liquidcross on 2009-10-01
I'm getting that error when trying to run an rsync script to backup my music folder to an external drive. I've heard that the problem is caused by hidden files and folders, and I can get around it by excluding those folders...but *how* do I exclude them?

Here's the script:

```
#!/bin/sh
SOURCE_DIRS="/sourcefolder"
TARGET_DIR="/backupfolder"

# if the external drive is not there, complain and stop
if [ ! -e "$TARGET_DIR" ]
then
echo Target directory does not exist!
exit
fi

IFS=:

pushd .
cd ~/
/usr/bin/rsync -E --delete --progress -av $SOURCE_DIRS "$TARGET_DIR"
popd
```

---

### Post by StuartN on 2009-10-02
> **liquidcross said:**
> *how* do I exclude them?

Add --exclude options to the rsync command, for instance you probably want to exclude the hidden Gnome virtual filing system with **--exclude ~/.gvfs** so your command would become:

```
/usr/bin/rsync -E --delete --progress -av --exclude ~/.gvfs $SOURCE_DIRS "$TARGET_DIR"
```

---

### Post by mdurham on 2009-10-02
> **StuartN said:**
> Add --exclude options to the rsync command, for instance you probably want to exclude the hidden Gnome virtual filing system with **--exclude ~/.gvfs** so your command would become:

```
/usr/bin/rsync -E --delete --progress -av --exclude ~/.gvfs $SOURCE_DIRS "$TARGET_DIR"
```

would the switch use '='? **--exclude=~/.gvfs**

---

