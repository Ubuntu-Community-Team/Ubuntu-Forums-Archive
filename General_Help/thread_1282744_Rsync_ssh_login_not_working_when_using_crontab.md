---
title: "Rsync ssh login not working when using crontab"
date: 2009-10-04
forum: General Help
---

### Post by Portable_Jim on 2009-10-04
I have tried to set up a backup system using Rsync (from [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)). I created the backups with my desktop system backing up itself and my laptop (also running ubuntu). However when I run rsync, backup of the laptop fails with
```
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(600) [receiver=3.0.5]
```I have set up a passphrase-less key pair on the desktop (called james-quad-core) and transferred it over to the laptop (called james-eeepc), and issuing
```
ssh james-eeepc.local
```from a root shell logges in without any confirmation or user interaction (i.e. password-less keys works).

When I ran the crontab command from a root shell, the bakup worked perfectly. However when crontab ran it (as root) it gave the error message above.

The backup script is (/root/backup/backup_script_eeepc):
```
#!/bin/bash
# ----------------------------------------------------------------------
# mikes handy rotating-filesystem-snapshot utility
# ----------------------------------------------------------------------
# this needs to be a lot more general, but the basic idea is it makes
# rotating backup-snapshots of /home whenever called
# ----------------------------------------------------------------------

unset PATH    # suggestion from H. Milz: avoid accidental use of $PATH

# ------------- system commands used by this script --------------------
ID=/usr/bin/id;
ECHO=/bin/echo;

MOUNT=/bin/mount;
RM=/bin/rm;
MV=/bin/mv;
CP=/bin/cp;
TOUCH=/bin/touch;
DIRNAME=/usr/bin/dirname

RSYNC=/usr/bin/rsync;

# ------------- file locations -----------------------------------------

MOUNT_DEVICE='-U b3304305-b478-4fb9-ba78-1df301adbde4';
SNAPSHOT_RW=/root/snapshot;
SUBFOLDER='eeepc'
FILTER='backup_rule_eeepc';
SOURCE='root@james-eeepc.local:/'

# ------------- the script itself --------------------------------------

# make sure we're running as root
if (( `$ID -u` != 0 )); then { $ECHO "Sorry, must be root.  Exiting..."; exit; } fi

# attempt to remount the RW mount point as RW; else abort
$MOUNT -o remount,rw $MOUNT_DEVICE $SNAPSHOT_RW ;
if (( $? )); then
{
    $ECHO "snapshot: could not remount $SNAPSHOT_RW readwrite";
    exit;
}
fi;


# rotating snapshots of /home (fixme: this should be more general)

# step 1: delete the oldest snapshot, if it exists:
if [ -d $SNAPSHOT_RW/$SUBFOLDER/daily.3 ] ; then            \
$RM -rf $SNAPSHOT_RW/$SUBFOLDER/daily.3 ;                \
fi ;

# step 2: shift the middle snapshots(s) back by one, if they exist
if [ -d $SNAPSHOT_RW/$SUBFOLDER/daily.2 ] ; then            \
$MV $SNAPSHOT_RW/$SUBFOLDER/daily.2 $SNAPSHOT_RW/$SUBFOLDER/daily.3 ;    \
fi;
if [ -d $SNAPSHOT_RW/$SUBFOLDER/daily.1 ] ; then            \
$MV $SNAPSHOT_RW/$SUBFOLDER/daily.1 $SNAPSHOT_RW/$SUBFOLDER/daily.2 ;    \
fi;

# step 3: make a hard-link-only (except for dirs) copy of the latest snapshot,
# if that exists
if [ -d $SNAPSHOT_RW/$SUBFOLDER/daily.0 ] ; then            \
$CP -al $SNAPSHOT_RW/$SUBFOLDER/daily.0 $SNAPSHOT_RW/$SUBFOLDER/daily.1 ;    \
fi;

# step 4: rsync from the system into the latest snapshot (notice that
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
$RSYNC                                    \
    -va --delete --delete-excluded                    \
    --filter="merge $($DIRNAME $0)/$FILTER"                \
    $SOURCE $SNAPSHOT_RW/$SUBFOLDER/daily.0/ ;

# step 5: update the mtime of daily.0 to reflect the snapshot time
if [ -d $SNAPSHOT_RW/$SUBFOLDER/daily.0 ] ; then            \
$TOUCH $SNAPSHOT_RW/$SUBFOLDER/daily.0 ;                \
fi

# and thats it for home.

# now remount the RW snapshot mountpoint as readonly

$MOUNT -o remount,ro $MOUNT_DEVICE $SNAPSHOT_RW ;
if (( $? )); then
{
    $ECHO "snapshot: could not remount $SNAPSHOT_RW readonly";
    exit;
} fi;
```The crontab line:
```
3 9    * * *    root    cd / && run-parts --report --verbose /etc/cron.nightly > /root/backup/logs/backup_log_cronlog 2> /root/backup/logs/backup_log_cronlog_error
```The backup job (referred to by a file in /etc/cron.nightly) (/root/backup/backup_script):
```
#!/bin/bash
echo "Backing up..."
echo "Backing up quad-core"
/root/backup/backup_script_quadcore > /root/backup/logs/backup_log_quadcore 2> /root/backup/logs/backup_log_quadcore_error && echo "Backed up quad-core"
echo "Backing up eee-pc"
/root/backup/backup_script_eeepc > /root/backup/logs/backup_log_eeepc 2> /root/backup/logs/backup_log_eeepc_error && echo "Backed up eee-pc"
echo "Done backing up, so dating the run"
date >> /root/backup/logs/backup_log_timestamp
```

---

### Post by XCan on 2009-10-05
Have you tried manually specifying the location of your keyfile with the ```
 -i /path/to/keyfile/ 
``` flag?

---

### Post by Portable_Jim on 2009-10-05
> **XCan said:**
> Have you tried manually specifying the location of your keyfile with the ```
 -i /path/to/keyfile/ 
``` flag?
Thanks. That got me on the right track.

The solution:
Adding
```
--rsh="ssh -i/path/to/keyfile/ "
```to the rsync command.

The keyfile to put in is the one that was generated by ssh-keygen. It is usually in ~/.ssh. There would be 2 files "keyfile" and "keyfile.pub", use "keyfile".

---

### Post by Portable_Jim on 2009-10-05
Now, What is the easiest way to mark a thread as solved?

---

### Post by cariboo on 2009-10-05
Go to thread tools at the top of the page to mark it solved. I've already done it for you.

---

