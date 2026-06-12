---
title: "Problem with backup using tar"
date: 2010-05-01
forum: General Help
---

### Post by mortalapeman on 2010-05-01
I am trying to back up my system to a FAT32 external HD. I wanted to back up all my previous settings and config files before going 10.04 incase something went wrong. This is my script.

sudo tar -cvpz --ignore-failed-read --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/home/eric/Downloads --exclude=/home/eric/Music --exclude=/home/eric/Videos --exclude=/home/eric/Documents/E-Books / | split -d -b 3900m - /media/FantomHD/backup.tar.gz.

When i run this script the first archive shows up as type gzip, but the archive manager is not able to read it. All the splits after the first one have the type "program" and can not be opened by the archive manager.

Before opening the archive manager, the first gzip file says it has 3.8 gigs. when i open it, it says the contained file is only 173 MB. Trying to open that file is the one that cannot be read by the archive manager.

My terminal had this error on the last line: "split: /media/FantomHD/backup.tar.gz.03: Input/output error"

Is there something wrong with my script? Is is it something to do with my hardware messing up when trying to deal with large amounts of data.

Any insight or help is appreciated. Thanks!

---

### Post by mortalapeman on 2010-05-02
bump

---

### Post by lavinog on 2010-05-02
I think that because of the way you are using split, you will need to join all of the files together first then extract
basically you are creating one big tar.gz file, then splitting it up.

To join the files use cat
```

cat backup.tar.gz* >backup_full.tar.gz

```

---

