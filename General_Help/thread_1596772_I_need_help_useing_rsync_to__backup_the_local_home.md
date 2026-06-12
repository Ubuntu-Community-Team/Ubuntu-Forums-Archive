---
title: "I need help useing rsync to  backup the local home directory"
date: 2010-10-14
forum: General Help
---

### Post by jefisme03 on 2010-10-14
I went ahead and created this directory

mkdir /tmp/rsync-backup

and, ran this

rsync –av /home /tmp/rsync-backup


this is the result 

rsync: link_stat "/–av" failed: No such file or directory (2)
skipping directory home
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

any help on what this means would be appreciated.

---

### Post by CharlesA on 2010-10-14
Should have worked. Try this:

```
rsync -av /home/* /tmp/rsync-backup/
```

---

### Post by jefisme03 on 2010-10-14
i retyped the command and this worked tho i see no difference in the commands

rsync -av /home /tmp/rsync-backup

---

### Post by CharlesA on 2010-10-14
It could have had a typo or something. Not sure.

Glad it's working now.

---

### Post by Hakunka-Matata on 2010-10-14
> rsync &#8211;av /home /tmp/rsync-backup
rsync -av /home /tmp/rsync-backup

Your first typed command as compared to the second one you typed, I don't know what character the longish dash is in the first command, but it's not the same character as the one in the second (the one that worked) command.

---

### Post by drdos2006 on 2010-10-14
There are other ways to use rsync as well.
```

#!/bin/bash

##    sudo rsync -rltDvu --modify-window=1 --progress --delete --delete-excluded --exclude-from=/home/user1/Documents/backup_install.txt  /media/sda3/InstallPrograms  /media/sdd/InstallPrograms

sudo bash 	/home/user1/Documents/MountServerShares.sh

sudo rm 	/home/user1/Documents/backup-log-var.txt
sudo 		apt-get autoclean
sudo rsync --verbose --delete-after  --recursive  --archive --modify-window=1 --times --update  --delete-after --progress --itemize-changes --log-file=backup-log-var.txt   /var/cache/apt/archives/  /media/sda1-320G/Install/Ubuntu-Work-In-Progress/var_cache_apt_archives/    

```

If you want to backup your whole /home directory, include the hidden files as well..
/home/user1/.kde
/home/user1/.mozilla  etc..
Check the man rsync pages....
regards

---

