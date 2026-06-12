---
title: "mounting alternative devices on same mount point?"
date: 2010-12-13
forum: General Help
---

### Post by ceperman on 2010-12-13
I have two USB HDDs I use alternatively as a backup drive. Both are defined in /etc/fstab to mount at /backup, although only one will ever be plugged in at any time:

# backup-a /dev/sd?1 (USB HDD)
UUID=484d928c-d955-4a36-ae45-595939e3ebcc /backup ext3 defaults,nobootwait   0 0
# backup-b /dev/sd?1 (USB HDD)
UUID=143d807d-37a4-412e-b5d1-79e4d83d3971 /backup ext3 defaults,nobootwait   0 0

The mount point /backup is defined in the root partition. An rsync job periodically copies data to this device. One downside of this setup is that if for some reason the USB HDD fails to mount to /backup, the rsync copies to the root partition which could potentially fill it up.  

This scheme worked fine on Ubuntu 8.04. However, when a recent upgrade to 10.04 hosed my system, I took advantage of the rebuild to define /backup in its own partition, to avoid the problem mentioned above. So now I have an additional entry in fstab:

# /backup was on /dev/sda6 during installation (partition)
UUID=9223f573-8ba9-4cec-823e-bebea7f8ad27 /backup ext3 defaults 0 2

What I want is that the USB HDD will be mounted as /backup if present, otherwise the /dev/sda6 partition will be mounted as /backup instead.

However, this doesn't happen. Regardless of the order in fstab, the /dev/sda6 partition always gets mounted at boot time even if one of the HDDs is present. I can manually mount the USB HDD, but I want it to happen automatically.

Is this possible to do this?

Chris

---

### Post by ragtag on 2010-12-13
An easier way to avoid your original problem would probably have been to add a simple check to see if the disk is mounted in your rsync script, and have it not run rsync if there is no disk mounted to /backup. :)

That would solve your original problem of having you system disk accidentally fill up, because it tries to run backup to a mountpoint, where no disk is mounted.

---

### Post by Krytarik on 2010-12-14
> **ragtag said:**
> An easier way to avoid your original problem would probably have been to add a simple check to see if the disk is mounted in your rsync script, and have it not run rsync if there is no disk mounted to /backup. :)

That would solve your original problem of having you system disk accidentally fill up, because it tries to run backup to a mountpoint, where no disk is mounted.
You could check if a particular file which lies on the backup drive exists at the mount point, like this:
```
if [ -f /backup/TESTFILE ]; then
```
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)
[http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html)

---

### Post by ceperman on 2010-12-14
I've used your suggestion to solve the problem.

As a better idea - hopefully! - instead of testing for the presence of a particular marker file (which could get lost among the backed-up data files), I discovered the 'mountpoint' command. This returns zero if a file system is actually mounted at the point specified, or non-zero if not.

So my script is now:
```
mountpoint -q /backup
if [ $? -ne 0 ]; then
  sudo mount /backup
fi
mountpoint -q /backup
if [ $? -eq 0 ]; then
  sudo rsync -av --progress --delete --log-file=/home/chris/backuplog/rsync_backup_$(date +%Y%m%d).log /shared/ /backup
else
  echo 'Backup device is not mounted - backup aborted' > /home/chris/backuplog/rsync_backup_$(date +%Y%m%d).log
fi
```
and seems to do the trick.

Many thanks,
Chris

---

### Post by Krytarik on 2010-12-14
Good to know!
Though I would put it this way, it spares the execution of one command;):
```
mountpoint -q /backup
if [ $? -ne 0 ]; then
  sudo mount /backup
  mountpoint -q /backup
fi
if [ $? -eq 0 ]; then
  sudo rsync -av --progress --delete --log-file=/home/chris/backuplog/rsync_backup_$(date +%Y%m%d).log /shared/ /backup
else
  echo 'Backup device is not mounted - backup aborted' > /home/chris/backuplog/rsync_backup_$(date +%Y%m%d).log
fi
```

---

