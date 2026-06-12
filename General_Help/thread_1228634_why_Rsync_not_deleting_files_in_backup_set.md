---
title: "why Rsync not deleting files in backup set?"
date: 2009-08-01
forum: General Help
---

### Post by Ascenti0n on 2009-08-01
Hi

I've have been torn between using sbackup and rsync to backup files both localy and remote.

I have 2 hard drives each with 2 partitions. At the moment I just want to incrementally backup a whole folder on one partition to another, which I do using this command:

> rsync -a /media/DataFiles/* /media/Backups/DataFiles/

but I noticed if a file gets deleted in the /media/DataFiles/ folder, it does not get deleted in the /media/Backups/DataFiles folder, having previously been backed up.

I know there is a --delete switch, but I'm nervous to use it because I am not confident of making no mistakes. Can someone show me what proper command should be pls.

thanks

---

### Post by TuckLive on 2009-08-01
I use 

```
sudo rsync --delete -azvv
```

and here is a link:

[https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

---

