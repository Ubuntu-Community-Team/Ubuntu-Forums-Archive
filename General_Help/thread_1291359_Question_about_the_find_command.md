---
title: "Question about the find command"
date: 2009-10-14
forum: General Help
---

### Post by malarie on 2009-10-14
Good day,

i have rsync running evey night as a backup tool  between 2 servers.


Since I only keep the backups for  15 days, i have setup a cronjob to clean  backups  older than 15 days..   I do this using the command find..

/usr/bin/find  /backup/PATH -type f -mtime +15 -exec rm {} \;
sleep 5  <--(please no comment)
/usr/bin/find  /backup/PATH -type d -mtime +15 -exec rmdir {} \;

the script does not work because  I Think rsync checks all the files before syncing. Hence, the files are accessed everyday.

Is there a better way to do this? I've checked the options atime and ctime but it seems they only check the lase access status of these files..

Thanks.

---

### Post by StuartN on 2009-10-14
> **malarie said:**
> I Think rsync checks all the files before syncing. Hence, the files are accessed everyday.

That would only change the atime (which you could disable by mounting with the noatime option), but rsync often incorrectly leaves newly created files with the date and time of the backup process, instead of the mtime of the original file. This can be a permission problem (mounting the destination with uid=me,gid=me might fix it). Have a look at your backups with **ls -l** to see what their apparent modification times are.

But if mtime is written correctly then your script will immediately delete any file that is older than 15 days, as soon as it is backed up. Rotating the backups (with hardlinks to save space) might work better, because you would be deleting by date of backup.

---

### Post by malarie on 2009-10-14
I did,   all the files keep their creation time, mbutthe LAST Access is like last night.. Ill check again tomorrow morning. Im home atm.

---

