---
title: "Hard Drive Backup Error?"
date: 2012-02-09
forum: General Help
---

### Post by Damascushead on 2012-02-09
I just used tar to back up my entire root directory, and I mainly used the following community source as a reference.

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

This is the command list that I entered...

```

tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / 
```It finished its work yet returned the following message at the end

```
tar: Exiting with failure status due to previous errors
```
Because of this error am not sure if this backed up correctly. I checked the location of the new compressed file and it seems like a perfectly fine tar file.

Any suggestions would be appreciated. Thanks!

---

### Post by Azdour on 2012-02-10
Hi,

When I use tar with the -v option I redirect the output to a log file, e.g.

```
tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / > /var/log/mybackup.log 2>&1
```

The 2>&1 part redirects all errors to the log as well.

The error 'tar: Exiting with failure status due to previous errors' is probably down to it not being able to archive a file or directory. In which case it should report it and then skip it, continuing on only to report that it had encountered an error at the end of the tar.

The log file should allow you to see what the error was on so that you can check yourself whether or not the error is serious or not.

---

### Post by Damascushead on 2012-02-10
Thank you for this, i will redirect the output. I briefly thought about it before, but was unsure if it would also redirect the tar backup as well as the log information. 
 
It makes sense that the archive failure was somewhere back on a small directory, but it just confused me that it showed up at the end. Wasn't sure if the entire backup failed :).

---

