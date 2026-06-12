---
title: "rsync vackup to remote server of a large dataset"
date: 2010-06-18
forum: General Help
---

### Post by mack4 on 2010-06-18
I have cygwin on Windows XP running rsync to remote Ubuntu server over ssh using ADSL.

My data set is about 20Gb! But, Cygwin will backup incrementally, so after the first backup the process should be relatively quick.

With ADSL the first backups will take too long. I was thinking about doing the first backup by copying files to an external hard drive then attaching the hard drive to my remote server and copying the files. The idea being that rsync will pick up the files as if it had created them in the first instance. The incremental backups will then pickup from there.

Does anyone have any experience with this and/or can provide any advice? The external hd is fat-32 which is okay with Windows and should be okay with Ubuntu? From XP right click copy and then paste keeps the file dates intact on the external hd - is this enough to get rsync going incrementally?

---

### Post by gzarkadas on 2010-06-18
If I remember well, copying your files to fat32 does not preserve permissions. This will most probably be a problem (but I haven't done it actually, so this is a guess).

If permissions in cygwin are the same for all files, you can invoke `chmod' and `chown' with the -R switch in the Ubuntu box after the copying. But the fact that directories have different set of permissions from normal files  (for example 755 vs 644) perplexes things a little, so you will have to do on the destination box the following:
```

cd <directory-where-files-were-copied>
chown -R <user>:<group> *
find -type d -exec chmod <enter-the-dir-mode-here> {} ';'
find -type f -exec chmod <enter-the-file-mode-here> {} ';'

```_I would suggest to try another strategy:_ Make an archive of all your data, using tar and copy the archive onto the external disk; then extract the archive contents in the target system. See `man tar' for selecting the write options for creation/extraction.

---

