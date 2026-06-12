---
title: "Automated home backups"
date: 2010-01-01
forum: General Help
---

### Post by ardchoille42 on 2010-01-01
It is my opinion that the user home directory is one of the most important directories of any *nix system. The rest of the system can be reinstalled from the source media at any time, but the user home directory can only be restored from an existing backup. The problem with backups is that many people don't perform them as often as they should.

In light of this, I have written a simple bash script that makes a backup archive of $HOME:

```
#!/bin/bash
# Filename: mybackups.sh
# Version: 0.8
# Author: Ian MacGregor (aka ardchoille)
# License: GPL
# Description: This script makes backup archives of $HOME

# Edit this to reflect your preferred destination directory
backupdir="/mnt/sdb1/archives/personal"

# Edit this to reflect your preferred temporary file name
backuptemp="temp.tar.bz2"

# Edit this to reflect your preferred final file name
# See man strftime for options other than %Y%m%d
backupfile="backups-$(date +%Y%m%d).tar.bz2"

# Remove any existing backup files
rm -f $backupdir/backups*

# Change directory
cd /home

# Tar up all files in $HOME
tar -cjf $backupdir/$backuptemp --exclude='.gvfs' $USER

# Change the path of the tarball
mv $backupdir/$backuptemp $backupdir/$backupfile

# Done
exit
```

Remember to replace $USER in the above script with your username. The resulting file will be named, for example, backups-20091231.tar.bz2 and I highly recommend running this script in a cronjob for automated backups. Please see [my crontab tutorial]("http://ardchoille42.blogspot.com/2009/04/crontab-tutorial.html") for more information about cronjobs.

I'm posting this in the hopes that it will be of use to someone.

[COLOR="Red"]UPDATE[/COLOR]: January 1, 2010 - Updated the script to remain silent during removal of old backup file.

[COLOR="Red"]UPDATE[/COLOR]: January 3, 2010 - Updated the script to fix backup file removal bug.

---

### Post by dhillonv10 on 2010-01-01
Thanks a bunch, backup scripts are always a help

---

### Post by CharlesA on 2010-01-01
I've got a script of my own, but I use rsync not tar.

---

### Post by dcstar on 2010-01-01
> **ardchoille42 said:**
> It is my opinion that the user home directory is one of the most important directories of any *nix system. The rest of the system can be reinstalled from the source media at any time, but the user home directory can only be restored from an existing backup. The problem with backups is that many people don't perform them as often as they should.
.........

The problem with backups is that most people do not do them at all. Any automated backup "solution" needs to be very resilient, things like ensuring mounted external destination devices are actually mounted are essential, along with 100% reliable reporting of success or failure - otherwise people may be lulled into a false sense of security that their data is actually safe.

It can be better to use tools like **unison **so people can simply initiate backups of their data and **know** that they have been successful.

---

