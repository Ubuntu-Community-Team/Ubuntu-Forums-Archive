---
title: "Help with rsync to NAS over SSH"
date: 2010-09-20
forum: General Help
---

### Post by behindtheeye on 2010-09-20
Hi,

I've bought a NAS (Western Digital My Book World Edition 1TB) which I want to use to make backups (preferably incremental) of some important files.

After much deliberation in finding suitable backup software it seems like good old rsync is the best thing for the job (backintime struggles to copy to remote locations?)

I have enabled SSH on the NAS config. I'm using the following command to do a test run on a small folder:

```
sudo rsync -azvv -e ssh /home/matt/Careers/ admin@192.168.1.100:/public/AutoBackup/

```

And I get the following error:

```
admin@192.168.1.100's password: 
sending incremental file list
rsync: mkdir "/public/AutoBackup" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(567) [receiver=3.0.2]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

```

The location I want to backup to appears in Nautilus as either: smb://192.168.1.100/public/AutoBackup or smb://mybookworld/public/AutoBackup

Anyone know where I'm going wrong here? I'm sure it's probably something simple but I can't crack it. I've tried variations on the destination folder such as admin@192.168.1.100:/AutoBackup/ without success.

Alternatively, any other software solutions would be welcomed!

Thanks!

---

### Post by behindtheeye on 2010-09-21
Gentle nudge!

---

### Post by behindtheeye on 2010-09-22
Last chance saloon!

---

### Post by luvshines on 2010-09-22
See if this helps :)

[http://ubuntuforums.org/showthread.php?t=599805](http://ubuntuforums.org/showthread.php?t=599805)

---

### Post by behindtheeye on 2010-09-23
Thanks, I will try when I get home!

---

