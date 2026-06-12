---
title: "Make a backup script to use with chron ?(rsync ?)"
date: 2011-03-10
forum: General Help
---

### Post by svavart on 2011-03-10
I'm trying to make a backup script with rsync that 
backups "/opt/example" to /mnt/sharedfolder/backup

And with each output the name would show the date of the 
backup & time. Then there would be 5 backups each time before the oldest would get replaced.
-------------------------------------------------------------------
I found something that I think does what I need but every time I run it I get this message.
```
rsync error: syntax or usage error (code 1) at main.c(1511) [Receiver=3.0.7]
./backupscript.sh: 65: /mnt/hgfs/bminecraft/: Permission denied
```

BTW /mnt/hgfs/bminecraft/ is chmoded to 755 and yes that is the correct path.

```
#!/bin/bash
# ----------------------------------------------------------------------
# mikes handy rotating-filesystem-snapshot utility
# ----------------------------------------------------------------------
# this needs to be a lot more general, but the basic idea is it makes
# rotating backup-snapshots of /home whenever called
# ----------------------------------------------------------------------

unset PATH	#  avoid accidental use of $PATH

# ------------- system commands used by this script --------------------
ID=/usr/bin/id;
ECHO=/bin/echo;

MOUNT=/bin/mount;
RM=/bin/rm;
MV=/bin/mv;
CP=/bin/cp;
TOUCH=/bin/touch;

RSYNC=/usr/bin/rsync;


# ------------- file locations -----------------------------------------

MOUNT_DEVICE=/opt/craftbukkit/;
SNAPSHOT_RW=/mnt/hgfs/bminecraft/;



# ------------- the script itself --------------------------------------

# make sure we're running as root
if (( `$ID -u` != 0 )); then { $ECHO "Sorry, must be root.  Exiting..."; exit; } fi



# rotating snapshots of /backup 

# step 1: delete the oldest snapshot, if it exists:
if [ -d $SNAPSHOT_RW/backup/hourly.3 ] ; then			\
$RM -rf $SNAPSHOT_RW/backup/hourly.3 ;				\
fi ;

# step 2: shift the middle snapshots(s) back by one, if they exist
if [ -d $SNAPSHOT_RW/backup/hourly.2 ] ; then			\
$MV $SNAPSHOT_RW/backup/hourly.2 $SNAPSHOT_RW/backup/hourly.3 ;	\
fi;
if [ -d $SNAPSHOT_RW/backup/hourly.1 ] ; then			\
$MV $SNAPSHOT_RW/backup/hourly.1 $SNAPSHOT_RW/backup/hourly.2 ;	\
fi;

# step 3: make a hard-link-only (except for dirs) copy of the latest snapshot,
# if that exists
if [ -d $SNAPSHOT_RW/backup/hourly.0 ] ; then			\
$CP -al $SNAPSHOT_RW/backup/hourly.0 $SNAPSHOT_RW/backup/hourly.1 ;	\
fi;

# step 4: rsync from the system into the latest snapshot (notice that
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
$RSYNC								\
-va --delete --delete-excluded				\
	--exclude=drasl/	
	/mnt/hgfs/bminecraft/ $SNAPSHOT_RW/backup/hourly.0 ;

# step 5: update the mtime of hourly.0 to reflect the snapshot time
$TOUCH $SNAPSHOT_RW/backup/hourly.0 ;

# and thats it for backup.
	$ECHO "endir";
	exit;
} fi;

```

---

### Post by kjohri on 2011-03-10
SNAPSHOT_RW=/mnt/hgfs/bminecraft/;

$RSYNC								\
-va --delete --delete-excluded				\
	--exclude=drasl/	
	/mnt/hgfs/bminecraft/ $SNAPSHOT_RW/backup/hourly.0 ;

I think the directory tree /mnt/hgfs/bminecraft/ is a part of source as well as destination and this may be causing the error. Replace the line SNAPSHOT_RW= ... with,
 
SNAPSHOT_RW=/mnt/hgfs/new/;

and try the script.

For more details on rsync,

[http://www.softprayog.in/tutorials/rsync-tutorial.shtml]("http://www.softprayog.in/tutorials/rsync-tutorial.shtml")

---

### Post by svavart on 2011-03-12
> **kjohri said:**
> SNAPSHOT_RW=/mnt/hgfs/bminecraft/;

$RSYNC								\
-va --delete --delete-excluded				\
	--exclude=drasl/	
	/mnt/hgfs/bminecraft/ $SNAPSHOT_RW/backup/hourly.0 ;

I think the directory tree /mnt/hgfs/bminecraft/ is a part of source as well as destination and this may be causing the error. Replace the line SNAPSHOT_RW= ... with,
 
SNAPSHOT_RW=/mnt/hgfs/new/;

and try the script.

For more details on rsync,

[http://www.softprayog.in/tutorials/rsync-tutorial.shtml]("http://www.softprayog.in/tutorials/rsync-tutorial.shtml")
Still got the same msg.

---

