---
title: "system backup/restore"
date: 2009-11-05
forum: General Help
---

### Post by coolgenes on 2009-11-05
I know there is a lot of talk of which backup program to use.  What about if you've settled on a program, let's say Back In Time or Remastersys, what directories do you copy so that in the event of breaking an installation one can restore the old info and save yourself a lot of headaches?  Do you save everything except /home?  does this save everything you need?  I store all my data on a separate system if that matters.

---

### Post by Giblet5 on 2009-11-05
I save /etc and /home after I dump the list of installed packages.

I use the tar command.

```
#!/bin/bash

cd $HOME
sudo dpkg -l | awk '{ print $2 }' | sed -e '1,5d' > packages.list
tar -cpjf /media/Bups/backup.tar.bz2 /etc /home && echo Successful && exit 0

echo "Backup failed" && exit 1
```

The restore process involves extracting the list of installed packages, installing those packages, restoring all of the files, followed by
```
sudo bash
sync;sync;reboot -f
```

---

### Post by coolgenes on 2009-11-13
does anyone back up their systems?

---

### Post by kubug on 2009-11-13
I do. I use sbackup (Simple Backup) and it does what I need it to do. I have used nssbackup (Not So Simple Backup) but it keeps failing to do the backup, so I removed it again.

sbackup is easy to setup and has done a decent job for me. Can't say that I needed to use the restore feature yet, but I have done a test and it seemed to have worked.

---

