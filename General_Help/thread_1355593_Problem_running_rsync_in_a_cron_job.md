---
title: "Problem running rsync in a cron job"
date: 2009-12-15
forum: General Help
---

### Post by maddog2050 on 2009-12-15
Hi,

I'm having a problem whilst running the following script from within a cron job on Ubuntu Server 9.04. The problem I'm having is that rsync exits with exit code 141 most of the time, I have looked at the the rsync manual and it doesn't have an exit code of 141.

Does anyone know what the problem is or how I can fix my script so that it works? As it works when I run it from the console.

Thanks

Adam

```

#!/bin/bash

backup () {
	until [ $B_ERROR = 20 ] || [ $B_ERROR = 0 ] || [ ! $B_SLEEPERROR = 0 ]; do
		
		rsync $B_OPTS $B_DIR $B_USER@$B_SERVER::$B_USER/current
		B_ERROR=$?

		echo RSYNC Exit Code = $B_ERROR>>$B_LOGFILE

		if [ ! $B_ERROR = 20 ]; then
			
			sleep $B_SLEEPTIME
			B_SLEEPERROR=$?

			echo SLEEP Exit Code = $B_SLEEPERROR>>$B_LOGFILE

			if [ ! $B_SLEEPERROR = 0 ]; then
				B_ERROR=-1
			fi
		fi
	done
}

# username
B_USER=someuser

# directory to backup
B_DIR=/

# speed in KBPS, 0 = unlimited
B_BWLIMIT=0

# max file size
B_MAXSIZE=1M

# excludes file - this contains a wildcard pattern per line of files to exclude
B_EXCLUDES=/somedir/excludes
B_EXCLUDES_NORMAL=/somedir/excludes-normal
B_EXCLUDES_ADDITIONAL=/somedir/excludes-additional

# the name of the backup machine
B_SERVER=somestoragesolution.com

# your password on the backup server
export RSYNC_PASSWORD=somepassword
export RSYNC_PARTIAL_DIR=.rsync-tmp

# logfile
B_LOGFILE=/somedir/backup-`date +%Y%m%d-%H%M%S-%N`.log

# eMail Settings
E_SERVER=smtp.someserver.com
E_FROM=root@somedomain.com
E_TO=user@somedomain.com
E_SUBJECT="Backup of XXXYYYZZZ"

# backup dir
B_BACKUPDIR=`date +%Y/%m/%d`

# other settings
B_ERROR=-1
B_SLEEPERROR=0
B_SLEEPTIME=1s

B_OPTS_NORMAL="-vv --archive --partial --fuzzy --force --ignore-errors 
               --compress-level=9 --exclude-from=$B_EXCLUDES --backup 
               --backup-dir=/$B_BACKUPDIR --bwlimit=$B_BWLIMIT 
               --log-file=$B_LOGFILE --progress --delete --delete-after"

B_OPTS_ADDITIONAL="--delete-excluded"

# Backup OS
cat $B_EXCLUDES_NORMAL >$B_EXCLUDES
cat $B_EXCLUDES_ADDITIONAL >>$B_EXCLUDES

B_OPTS=$B_OPTS_NORMAL
backup

echo B_ERROR=$B_ERROR>>$B_LOGFILE

if [ $B_ERROR = 0 ]; then

	B_ERROR=-1
	B_SLEEPERROR=0

	# Backup OS + Data
	cat $B_EXCLUDES_NORMAL >$B_EXCLUDES

	B_OPTS="$B_OPTS_NORMAL $B_OPTS_ADDITIONAL"
	backup
fi

echo Sending eMail>>$B_LOGFILE
sendEmail -f $E_FROM -t $E_TO -u $E_SUBJECT -s $E_SERVER -m "Backup" -a $B_LOGFILE

```

---

### Post by revanb on 2009-12-15
When running cron jobs your usual environment is not preserved. Things like path for instance.

You should specify paths for everything and make sure environment variables that are needed are available.

This catches most people and there should be an easy way to keep your environment, but I don't know it?

---

### Post by maddog2050 on 2009-12-15
I have updated the script to have the full paths for all the executables but I'm still getting the same error.

Adam

---

### Post by revanb on 2009-12-15
If it works correctly when you run it manually and not when used in cron then there must be some environment variable or other "assuption" which is not valid under cron.

Are you sure rsync is getting the correct username and server names?

Good luck!

---

### Post by john newbuntu on 2009-12-15
Make a small change in your crontab file.  Edit it and add the -x option to bash and output the result to another file. like:
50 9 * * *   /bin/bash -x myscript.bash >> /home/<loginid>/myscript.out 2>&1

After it runs, inspect the myscript.out file and see if variables were set according to your expectation.

---

### Post by maddog2050 on 2009-12-15
Found the solution, I had to add >/dev/null 2>&1 to the rsync command as it is working since doing this. I also added it to the cron job it's self to be on the safe side.

Thanks

Adam

---

