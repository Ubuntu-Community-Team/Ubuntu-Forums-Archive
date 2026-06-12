---
title: "rsync scripting, bash help"
date: 2010-06-08
forum: General Help
---

### Post by jerome1232 on 2010-06-08
Okay so I'm no bash programmer, I've made a simple backup script that I want to try and add some functionality to.

Right now it creates an lvm snapshot volume, mounts it read only, then logs into my server via ssh, shuffles some directories around (incremental backups), then rsync's the snapshot volume via ssh. Finally it unmounts and removes the lvm snapshot volume, logs back into the ssh server and removes that oldest backup.

So my goals:

1) Add error checking (if the lvm volume fails to get created abort the script and send the log to root's system mail. If the ssh connection fails, abort the operation, remove the snapshot volume and abort the script sending mail to root. etc...

2) make it check to see if the incremental backups exist and adjust itself accordingly if they don't or only some do, maybe I had to wipe them out for one reason or another.

3) Get it to check to see if it's being run as root, if not abort and send a log to root user.

Here is the script, keep in mind I barely know what I'm doing! Maybe even some links to other well documented rsync scripts will help, I really just don't know how to implement the above goals.

```
#!/bin/bash

#
# Creating a snapshot volume so that the file-system is in a consi
# tent state
#
lvcreate -s direbane/data -n dataSnapshot -L 8G
mount /dev/direbane/dataSnapshot /mnt/dataSnapshot -o ro
#
# Moving old directories around on the server, I keep 4 days worth of
# changes around, backup.0 is the most recent
#
ssh backups@voiceserv 'mv -v /backup/backup.3 /backup/backup.tmp; mv -v /backup/backup.2 /backup/backup.3; mv -v /backup/backup.1 /backup/backup.2; mv -v /backup/backup.0 /backup/backup.1; mkdir -v /backup/backup.0'

#
# Doing the backup!
#
rsync -avz --delete-delay --exclude=.Trash* --link-dest=/backup/backup.1 /mnt/dataSnapshot/ backups@voiceserv:/backup/backup.0

#
#Cleanup
#
ssh data@voiceserv.homelinux.net 'rm -rfv /backup/backup.tmp'
umount /mnt/dataSnapshot
lvremove direbane/dataSnapshot
exit 0
```

---

### Post by oldfred on 2010-06-08
I think I know less than you, but I copied this from someone else. It is only a small part of what you want.

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi

---

### Post by jerome1232 on 2010-06-08
Thanks for the tip, after alot of googling I was able to come up with this, I haven't tested it yet (currently have a manually run backup going so don't want to interfere with it)

rsyncscript.sh
```
#!/bin/bash

# Check if we are root
if [ $UID -ne 0 ] ; then
	sh /usr/local/sendmail.sh "Rsync Backup Failed" "jeremy@localhost" "rsyncscript.sh ran as $(whoami) on $(date)"
	echo "Must be run as root, now sending a notification to the admin"
	exit 255
fi

#
# Creating a snapshot volume so that the file-system is in a consitent state
#

lvcreate -s direbane/data -n dataSnapshot -L 8G 2> /tmp/log/lvcreate
if [ -s /tmp/log/lvcreate ] ; then
	sh /usr/local/sendmail.sh "Rsync Backup Failed" "jeremy@localhost" "/tmp/log/lvcreate"
	cat /tmp/log/lvcreate >> /var/log/backup
	rm -f /tmp/log/lvcreate
	exit 254
fi

mount /dev/direbane/dataSnapshot /mnt/dataSnapshot -o ro 2> /tmp/log/mountSnapshot
if [ -s /tmp/log/mountSnapshot ] ; then
	sh /usr/local/sendmail.sh "Rsync Backup Failed" "jeremy@localhost" "/tmp/log/mountSnapshot"
	cat /tmp/log/mountSnapshot >> /var/log/backup
	rm -f /tmp/log/mountSnapshot
	lvremove -f direbane/dataSnapshot
	exit 253
fi

#
# Moving old directories around on the server, I keep 4 days worth of
# changes around, backup.0 is the most recent
#
[COLOR="Red"]ssh backups@voiceserv 'mv -v /backup/backup.3 /backup/backup.tmp; mv -v /backup/backup.2 /backup/backup.3; mv -v /backup/backup.1 /backup/backup.2; mv -v /backup/backup.0 /backup/backup.1; mkdir -v /backup/backup.0' 2> /tmp/log/shuffle
if [ -s /tmp/log/shuffle ] ; then
	sh /usr/local/sendmail.sh "Rsync Backup Failed" "jeremy@localhost" "/tmp/log/shuffle"
	cat /tmp/log/shuffle >> /var/log/backup
	rm -f /tmp/log/shuffle
	umount /mnt/dataSnapshot
	lvremove -f direbane/dataSnapshot
	exit 252
fi[/COLOR]

#
# Doing the backup!
#
rsync -avz --delete-delay --exclude=.Trash* --link-dest=/backup/backup.1 /mnt/dataSnapshot/ backups@voiceserv:/backup/backup.0 2> /tmp/log/rsyncbackup
if [ -s /tmp/log/rsyncbackup ] ; then
	sh /usr/local/sendmail.sh "Rsync Backup Failed" "jeremy@localhost" "/tmp/log/rsyncbackup"
	echo "Rsync Failed"
	cat /tmp/log/rsyncbackup >> /var/log/backup
	rm -f /tmp/log/rsyncbackup
	umount /mnt/dataSnapshot
	lvremove -f direbane/dataSnapshot
	exit 251
fi

#
#Cleanup
#
ssh data@voiceserv.homelinux.net 'rm -rfv /backup/backup.tmp'
umount /mnt/dataSnapshot
lvremove -f direbane/dataSnapshot
exit 0
```

sendmail.sh
```
#!/bin/bash
# script to send an email
email="$1"
subject="$2"
emailmessage="$3"

mail -s "$subject" "$email" < "$emailmessage"

exit 0

```

Looking for critique or "That won't work you idiot do it like this", I still want to modify the part highlighted in red to adjust itself if no directories exist (just run a regular rsync ) or only some of them exist and shuffle them around appropriately.

---

### Post by jerome1232 on 2010-06-09
edited new info.

---

### Post by jerome1232 on 2010-06-09
Hate to bump my own post again so early (only 8 hours) but I'm about to go to bed I think I'm mostly done, my only big issue remaining is sshfs mount options.

This is the part of my script that mounts the sshfs file-system

```
echo "Mounting backups@voiceserv:/backup on $backupmount" 
[COLOR="Blue"]sshfs -C backups@voiceserv:/backup $backupmount -o allow_other [/COLOR]
if (( $? )) ; then
	sh $sendmail "$subject" "$email" "Mounting remote servers backup directory failed $(date)" 
	echo "Mounting remote servers backup directory failed $(date)" 
	sh $cleanup 2 "$lvsnapshotmount" "$vg" "$lvsnapshot" 
	exit 252 
fi 
```

and the snippet that does the initial rsync (what I'm testing now)
```
echo "Detecting old backups"
if [ ! -d $backupmount/$backup.0 ] ; then
	echo "No old backups detected, doing initial backup"
	mkdir $backupmount/$backup.0
	rsync -a --exclude-from=$excludes $lvsnapshotmount/ $backupmount/$backup.0
	if (( $? )) ; then
		echo "Rsync Failed"
		sh $sendmail "$subject" "$email" "Rsync Failed"
		sh $cleanup 3 "$lvnsapshotmount" "$vg" "$lvsnapshot" "$backupmount"
		exit 251
	else
		echo "Initial Backup complete"
	fi
```


When I run the script I get this (it's still running but I'm sure there's more chown errors that will happen in the top level directory, this is 20 some odd GB's of data so I don't feel like waiting for every single error to show up)

```
sudo rsyncscript.sh 
Checking to see if /usr/local/bin/rsyncscript.sh is being run as root
  Logical volume "dataSnapshot" created
Mounting direbane/dataSnapshot on /mnt/dataSnapshot/
Success!

Mounting backups@voiceserv:/backup on /mnt/backup/
Success!
Detecting old backups
No old backups detected, doing initial backup
rsync: chown "/mnt/backup/main-data-backup.0/." failed: Permission denied (13)
rsync: chown "/mnt/backup/main-data-backup.0/3.5" failed: Permission denied (13)
rsync: chown "/mnt/backup/main-data-backup.0/Documents" failed: Permission denied (13)
rsync: chown "/mnt/backup/main-data-backup.0/Documents/ink_files" failed: Permission denied (13)
rsync: chown "/mnt/backup/main-data-backup.0/Documents/netflix_files" failed: Permission denied (13)
rsync: chown "/mnt/backup/main-data-backup.0/Downloads" failed: Permission denied (13)
rsync: chown "/mnt/backup/main-data-backup.0/Downloads/D2-1.12A-enUS" failed: Permission denied (13)
```

---

### Post by jerome1232 on 2010-06-16
Well just in case anyone is interested I did get it working, sort of.

I think rsync was having issues chowning on the servers end because it's not running as root there but as a regular user.

I ended up just telling rsync to not preserve owner or group to avoid the chown errors, as to why that doesn't crop up when using regular ssh vs sshfs I have no idea.

So here is the final script, I realized the cron sends you an email with the output of the command being run so I disabled all the mail notifications i had built into the script.

/usr/local/bin/rsyncscript.sh
```
#!/bin/bash

#subject="Rsync Backup Failed"
#email="jeremy@localhost"

vg="direbane"
lv="data"
lvsnapshot="dataSnapshot"
lvsnapshotmount="/mnt/dataSnapshot/"
backupmount="/mnt/backup/"
backup="main-data-backup"
excludes="/home/jeremy/Documents/rsyncexcludes"
sendmail="/usr/local/bin/sendmail.sh"
cleanup="/usr/local/bin/cleanup.sh"

# Check if we are root
echo "Checking to see if $0 is being run as root"
if [ $UID != 0 ] ; then
	#sh $sendmail "$subject" "$email" "rsyncscript.sh ran as $(whoami) on $(date)" 
	echo "Must be run as root, now sending a notification to the admin" 
	exit 255 
fi 

#
# Creating a snapshot volume so that the file-system is in a consitent state
# Mounting the volume read only and mounting the servers backup directory via ssh.
#

lvcreate -s $vg/$lv -n $lvsnapshot -L 8G
if (( $? )) ; then
	#sh $sendmail "$subject" "$email" "Failed to create snapshot volume of direbane/data $(date)" 
	echo "Failed to create snapshot volume of direbane/data $(date)"
	exit 254 
fi 
echo "Mounting $vg/$lvsnapshot on $lvsnapshotmount" 
mount /dev/$vg/$lvsnapshot $lvsnapshotmount -o ro 
if (( $? )) ; then
	#sh $sendmail "$subject" "$email" "Mounting snapshot volume direbane/dataSnapshot failed $(date)" 
	echo "Mounting snapshot volume direbane/dataSnapshot failed $(date)" 
	sh $cleanup 1 "$lvsnapshotmount" "$vg" "$lvsnapshot" 
	exit 253 
fi 
echo "Success!" 
echo 
echo "Mounting backups@voiceserv:/backup on $backupmount" 
sshfs -C backups@voiceserv:/backup $backupmount -o workaround=rename,idmap=user,follow_symlinks,allow_root
if (( $? )) ; then
	#sh $sendmail "$subject" "$email" "Mounting remote servers backup directory failed $(date)" 
	echo "Mounting remote servers backup directory failed $(date)" 
	sh $cleanup 2 "$lvsnapshotmount" "$vg" "$lvsnapshot" 
	exit 252 
fi 
echo "Success!" 
	
#
# Moving old directories around on the server, I keep 4 days worth of
# changes around, backup.0 is the most recent
# Doing the backup if all moves and/or folders are successful and/or are in 
# correct locations
#
echo "Detecting old backups"
if [ ! -d $backupmount/$backup.0 ] ; then
	echo "No old backups detected, doing initial backup"
	mkdir $backupmount/$backup.0
	rsync -rlptD --exclude-from=$excludes $lvsnapshotmount/ $backupmount/$backup.0
	if (( $? )) ; then
		echo "Rsync Failed"
		#sh $sendmail "$subject" "$email" "Rsync Failed"
		sh $cleanup 3 "$lvnsapshotmount" "$vg" "$lvsnapshot" "$backupmount"
		exit 251
	else
		echo "Initial Backup complete"
	fi
else
	if [ -d $backupmount/$backup.3 ] ; then
	mv $backupmount/$backup.3 $backupmount/$backup.tmp
	echo "Moved $backup.3 to $backup.tmp"
	fi
	if [ -d $backupmount/$backup.2 ] ; then
	mv $backupmount/$backup.2 $backupmount/$backup.3
	echo "Moved $backup.2 to $backup.3"
	fi
	if [ -d $backupmount/$backup.1 ] ; then
	mv $backupmount/$backup.1 $backup.2
	echo "Moved $backup.1 to $backup.2"
	fi
	mv $backupmount/$backup.0 $backupmount/$backup.1
	echo "Moved $backup.0 to $backup.1"
	mkdir $backupmount/$backup.0
	echo "Created $backup.0"
	echo "Now doing incremental backup"
	rsync -rlptD --link-dest=$backupmount/$backup.1 --exclude-from=$excludes $lvsnapshotmount/ $backupmount/$backup.0
	if (( $? )) ; then
		echo "Incremental Backup failed"
		#sh $sendmail "$subject" "$email" "Rsync Failed"
		sh $cleanup 3 "$lvsnapshotmount" "$vg" "$lvsnapshot" "$backupmount"
		exit 251
	fi
fi
exit 0
```

/usr/local/bin/cleanup.sh
```
#!/bin/bash
#cleanup for rsyncscript.sh
step=$1
lvsnapshotmount=$2
vg=$3
lvsnapshot=$4
backupmount=$5

#echo "step is " $step
#echo "lvsnapshotmount is " $lvsnapshotmount
#echo "vg is " $vg
#echo "lvsnapshot is " $lvsnapshot
#echo "backupmount is " $backupmount

if [ $step = 1 ] ; then
	echo "Removing $lvsnapshot"
	lvremove -f $vg/$lvsnapshot 
fi
if [ $step = 2 ] ; then
	echo "Unmounting $lvsnapshotmount"
	umount -v $lvsnapshotmount
	sleep 1 
	echo "Removing $lvsnapshot"
	lvremove -f $vg/$lvsnapshot 
fi
if [ $step = 3 ] ; then
	echo "Unmounting sshfs mount $backupmount"
	fusermount -u $backupmount 
	echo "Unmounting $lvsnapshotmount"
	sleep 1
	umount -v $lvsnapshotmount 
	echo "Remvoing $lvsnapshot"
	lvremove -f $vg/$lvsnapshot 
fi
exit 0

```

and finally the excludes file

/home/jeremy/Documents/rsyncexcludes
```
.Trash*
lost+found
*.iso
*.img
*.vdi
```


I'm still open for any tips please, they would be very much appreciated.

---

