---
title: "How to make a backup script for rsync ???"
date: 2010-10-03
forum: General Help
---

### Post by Robert R on 2010-10-03
Hi i have ubuntu 10.04 and have installed rsync. I believe it is a tool to be used from the terminal because i see no GUI for it. I would like some help in creating backup scripts to do 
my backups. How would one go about starting to do this ??

1. What format or extension do i save the script in ??
2. Maybe a little help in starting the script like what command to use for source files and 
    how would i integrate using multiple sources and a destination??

If i have these steps wrong someone please point me in the right direction as i am fairly new to ubuntu.

Thanks in advance.

---

### Post by DeMus on 2010-10-03
> **Robert R said:**
> Hi i have ubuntu 10.04 and have installed rsync. I believe it is a tool to be used from the terminal because i see no GUI for it. I would like some help in creating backup scripts to do 
my backups. How would one go about starting to do this ??

1. What format or extension do i save the script in ??
2. Maybe a little help in starting the script like what command to use for source files and 
    how would i integrate using multiple sources and a destination??

If i have these steps wrong someone please point me in the right direction as i am fairly new to ubuntu.

Thanks in advance.

Also install grsync and you have the gui.

---

### Post by oldfred on 2010-10-04
Here is one example.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh

I added these two lines so I have current copies in my /home, as I only back up /home.

cp /etc/apt/sources.list ~/sources.list.backup
dpkg --get-selections > ~/ubuntu-files

Someone posted this, but I do not backup /etc, but do copy any manually edited config in /etc into a folder in /home so it gets backed up.

I backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script I wrote to generate the backup
List of sources:
5. sudo cp /etc/apt/sources.list ~/sources.list.backup
Installed applications list (to make it easy to reinstall everything)#
dpkg --get-selections | grep -v deinstall > ubuntu-files
or
6. dpkg --get-selections > ubuntu-files

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by drdos2006 on 2010-10-04
Here is how I back up my archives directory using the command :
bash backup-var.sh 
from the terminal.

Open a file and save the file as :  backup-var.sh

#!/bin/bash

sudo apt-get autoclean

sudo rsync --verbose --delete-after  --recursive  --archive --modify-window=1 --times --update   --progress --itemize-changes --log-file=backup-log.txt   /var/cache/apt/archives/*.deb  /media/sda1-320G/Install/Ubuntu-Work-In-Progress/var_cache_apt_archives/    


regards

---

### Post by Zimmer on 2010-10-04
> **Robert R said:**
> Hi i have ubuntu 10.04 and have installed rsync. I believe it is a tool to be used from the terminal because i see no GUI for it. I would like some help in creating backup scripts to do 
my backups. How would one go about starting to do this ??

1. What format or extension do i save the script in ??
2. Maybe a little help in starting the script like what command to use for source files and 
    how would i integrate using multiple sources and a destination??

If i have these steps wrong someone please point me in the right direction as i am fairly new to ubuntu.

Thanks in advance.
Lots of lovely reading in the above answers. All good.
I have used rsync from the command line and was looking for the same info.
This link answered my question today. I have tried a script based on my requirements and it works... yet to try the cron bit though...one step at a time..
[http://linuxbasement.com/content/backups-using-rsync-bash-cron](http://linuxbasement.com/content/backups-using-rsync-bash-cron)

---

### Post by Staffan Ericsson on 2010-10-04
rsnapshot is great :-)

.staffan

---

### Post by Robert R on 2010-10-05
> "Lots of lovely reading in the above answers. All good.
I have used rsync from the command line and was looking for the same info.
This link answered my question today. I have tried a script based on my  requirements and it works... yet to try the cron bit though...one step  at a time.." 

This information is really helpful, does anyone know of a linux book or such documentation that explains the scripting that is used as in the examples above. ??

---

### Post by surfer on 2010-10-05
i have a script that does incremental backups with rsync. the  [FONT="Courier New"]--link-dest[/FONT] option is magic!

this is the executable bash file ([FONT="Courier New"]rsync_backup.sh[/FONT])
```
#!/bin/bash

# a script that does incremental backups of a directory tree.




# edit source and destination path here.
# No trailing slashes!
SRC_PATH="/home/user/tmp/src"
DST_PATH="/home/user/tmp/bkp" 





# --------------------------------------------------------------------------------------------------------------------


HERE="$(dirname $(readlink -f ${BASH_SOURCE}))"

CURRENT_NAME="current_snapshot"
CURRENT_PATH="${DST_PATH}/${CURRENT_NAME}"

NOW=$(date +"%Y%m%d-%H%M%S")
DATE_PATH="${DST_PATH}/${NOW}"

EXCLUDE_FROM="${HERE}/rsync_backup.exclude"
RSYNC_OPTS=" --exclude-from=${EXCLUDE_FROM} -av ${SRC_PATH} ${DATE_PATH}"



initial_snaphsot()
{
  /bin/mkdir -p "${DATE_PATH}"
  /usr/bin/rsync ${RSYNC_OPTS}
  /bin/ln -s "${NOW}" "${CURRENT_PATH}"
}

incremental_snaphsot()
{
  /bin/mkdir -p "${DATE_PATH}"
  /usr/bin/rsync --link-dest "${CURRENT_PATH}" ${RSYNC_OPTS}
  /bin/rm -f "${CURRENT_PATH}"
  /bin/ln -s "${NOW}" "${CURRENT_PATH}"
}


main()
{
  if [ ! -d "${CURRENT_PATH}" ]; then
    # this is the initial snapshot
    initial_snaphsot
  else
    # incremental backup
    incremental_snaphsot
  fi
}



# --------------------------------------------------------------------------------------------------------------------

main

# --------------------------------------------------------------------------------------------------------------------


```


and a [FONT="Courier New"]rsync_backup.exclude[/FONT] file that contains:
```
tmp
.local
.gconf*
.gimp*
.kde*
.gnome*
.openoffice.org2
.mozilla*
.ssh
.subversion
.DCOPserver*
.gnupg
.X*
.x*
```

---

### Post by Zimmer on 2010-10-05
> **Robert R said:**
> This information is really helpful, does anyone know of a linux book or such documentation that explains the scripting that is used as in the examples above. ??

[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

Might help, I have not read it all yet, though :)

---

### Post by oldfred on 2010-10-05
Some info on bash, but each command you may have to use man to find details of the command.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[http://docs.thinkfree.com/docs/view.php?dsn=852556](http://docs.thinkfree.com/docs/view.php?dsn=852556)
[http://linuxcommand.org/](http://linuxcommand.org/)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)

from terminal:
man rsync

---

### Post by Robert R on 2010-10-06
Thanks Everyone

---

### Post by doublemeat on 2011-02-10
Don't forget ```
gconftool-2 --dump /apps/panel > ~/gnome-panel.settings
``` :D

> **oldfred said:**
> Here is one example.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh

I added these two lines so I have current copies in my /home, as I only back up /home.

cp /etc/apt/sources.list ~/sources.list.backup
dpkg --get-selections > ~/ubuntu-files

Someone posted this, but I do not backup /etc, but do copy any manually edited config in /etc into a folder in /home so it gets backed up.

I backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script I wrote to generate the backup
List of sources:
5. sudo cp /etc/apt/sources.list ~/sources.list.backup
Installed applications list (to make it easy to reinstall everything)#
dpkg --get-selections | grep -v deinstall > ubuntu-files
or
6. dpkg --get-selections > ubuntu-files

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

