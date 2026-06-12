---
title: "Simple Backup run script"
date: 2010-11-16
forum: General Help
---

### Post by Wtower on 2010-11-16
We have a small office Ubuntu file server and Simple Backup for our backup software on a removable usb hdd. The issue I had was that another person was responsible for connecting the disk and taking it away at the end of the day, completely unaware that there is a thing called mounting. This was a standard automatic mount/umount issue so oftenly described.

So I decided to write down my own first bash script in order to replace the standard /etc/cron.d/sbackup entry (and it works as far as I tested it). Basically what it does is carefully mount the disk, take backup, carefully unmount it and email an executive summary of the result.

I decided to post it as may be beneficiary for others. Use it at own risk, all feedback most welcome.

```

#!/bin/bash
# Forecasting Consultancy
# Simple Backup run script

# Configuration Section

# Backup disk
# Specify the disk to be mounted
# Make sure this is the removable one that is usually connected and that no 
# other removable is connected prior to this, or you will end up with a backup
# at a wrong place

DISK=/dev/sdc1

# Disk filesystem

DISKFS=ext4

# Mount point specified at sbackup
# DON'T put in anything stupid like /

MPOINT=/media/book

# Mail subject for success

SUBJ="Daily backup report for $HOSTNAME"

# Mail subject for failure

SUBJF="***Daily backup report for $HOSTNAME"

# Mail recipients

TO=mail@domain,mail2@domain

##############
# initiate
MOUNTED=`mount | grep "$DISK on $MPOINT"`
RESULT=""
if [ -z "$MOUNTED" ]; then #missing
	if [ ! -d $MPOINT ]; then
		mkdir $MPOINT
	fi
	LS=`ls $MPOINT`
	if [ -z "$LS" ]; then
		RESULT=`mount $DISK $MPOINT -t $DISKFS -o rw,nosuid,nodev,default_permissions`
	else
		RESULT="Critical error: $DISK is not mounted and $MPOINT not empty."
	fi
fi

# check
if [ ! -z "$RESULT" ]; then
	echo -e "\nATTENTION\n\nBackup has not been executed.\n\nBackup disk ($DISK) cannot be mounted on ($MPOINT):\n$RESULT\n" | mail -s "$SUBJF" $TO
	exit
fi

# execute
if [ -x '/usr/share/sbackup/sbackup-launch' ]; then
	/usr/share/sbackup/sbackup-launch
fi

# finalize
# check results
DIRINPLACE=false
SUCCESS=false
UMOUNT=false
DIREMPTY=false

if [ -d $MPOINT ]; then
	DIRINPLACE=true
	DATEPART=`date +%Y-%m-%d`
	LSFILE=`ls $MPOINT | grep $DATEPART`
	if [ ! -z "$LSFILE" ]; then
		SUCCESS=true
	fi
	RESULT=`umount $MPOINT`
	if [ -z "$RESULT" ]; then
		UMOUNT=true
		LS=`ls $MPOINT`
		if [ -z "$LS" ]; then
			DIREMPTY=true
			rm -rf $MPOINT
		fi
	fi
fi

# compose mail
TAIL=`tail --lines=2 /var/log/sbackup/sbackup.log`
if [ "$SUCCESS" == "true" ]; then
	SUBJFINAL=$SUBJ
	BODY="\nBackup has been successfully completed:\n$TAIL\n"
else
	SUBJFINAL=$SUBJF
	BODY="\nATTENTION: Backup has not been successfully completed:\n$TAIL\n"
fi
if [ "$DIRINPLACE" == "true" ]; then
	if [ "$UMOUNT" != "true" ]; then
		BODY="$BODY\nATTENTION: The backup disk ($DISK) has not been unmounted:\n$RESULT\n"
	fi
	if [ "$DIREMPTY" != "true" ]; then
		BODY="$BODY\nATTENTION: The mount point directory ($MPOINT) is not empty.\n"
	fi
else
	BODY="$BODY\nATTENTION: Backup disk is not mounted.\nPossible removal during process.\n"
fi
echo -e "$BODY" | mail -s "$SUBJFINAL" $TO

#EOF

```

Regards

---

