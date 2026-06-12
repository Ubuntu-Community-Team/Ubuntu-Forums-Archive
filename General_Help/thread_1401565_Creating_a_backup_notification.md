---
title: "Creating a backup notification"
date: 2010-02-08
forum: General Help
---

### Post by jessel on 2010-02-08
I have a scheduled backup that runs via anacron, and I currently am writing the output to a log file and mailing the output to root via local mail, see [http://ubuntuforums.org/showthread.php?t=1380262](http://ubuntuforums.org/showthread.php?t=1380262)
I have tried implemented a notification using libnotify, see [http://ubuntuforums.org/showthread.php?t=775170](http://ubuntuforums.org/showthread.php?t=775170)
Two problems:
1) I don't get a notification when anacron runs the backup script, I get a notification (sent to my primary user) when root runs a "test" notification script (I strip out the rsync command)
2) I don't think that this notificication will get delivered if another user is logged in when the backup script is run.

I have become accustomed to the notifications that I get from evolution calendar, and I know that if the computer is off when the alarm is to be triggered I still get the notification next time I log in.

For what its worth, I am running a Jaunty desktop computer for househould use, and there are two users.

/etc/cron.daily/backup:
#!/bin/sh
#
# man-db cron daily

########### following is for notification command 
init_notify() {
	user=`jesse`
	pids=`pgrep -u $user nautilus`
	for pid in $pids; do
		# find DBUS session bus for this session
		DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
		# use it
		export DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS
	done
}

notify() {
	if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
		init_notify
	fi
	
	title=$1
	text=$2
	urgency=$3
	timeout=$4
	
	if [ -z "$title" ]; then
		return
	fi
	if [ -z "$text" ]; then
		return
	fi
	if [ -z "$urgency" ]; then
		return
	fi
	if [ -z "$timeout" ]; then
		return
	fi
	
	notify-send "$title" "$text" -u $urgency -t $timeout
}
########### above is for notification ######################

rsync -vaxE --delete --ignore-errors / /.backup >> /var/log/backup.log
ret_val=$?
echo "[`date`] rsync completed with exit status $ret_val" >> /var/log/backup.log

notify "Mirror Backup:" "The daily mirror backup has just finished" critical 0

---

### Post by jessel on 2010-02-09
any comments would be appreciated

thanks

---

### Post by jessel on 2010-02-12
ok, so another thing I wanted to note is that I don't actually want to have the notification tell me every time the backup runs, what I'm looking to implement is a notification when I get an error. I know that I will not get a notification of an error, since I currently do not get the notification that the backup completed...

it seems like having an error notification as part of the backup task would be fairly common. all it takes would be a backup drive that is filled up. I would get error messages on syslog, but I don't that read on a daily basis. That is why something immediate would be ideal.

So again, any thoughts. I am certain I'm probably re-inventing the wheel, but I can't find a solution.

---

