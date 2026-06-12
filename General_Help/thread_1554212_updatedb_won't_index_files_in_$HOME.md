---
title: "updatedb won't index files in $HOME"
date: 2010-08-16
forum: General Help
---

### Post by strycat on 2010-08-16
when I do 

locate foo

it doesn't seem to find the file foo in /home/strycat/  this is the case for every file I've tried to locate in my home directory.

I did a sudo updatedb and tried again.  No such luck.

I checked my /etc/updatedb.conf file.

PRUNE_BIND_MOUNTS="yes"
# PRUNENAMES=".git .bzr .hg .svn"
PRUNEPATHS="/tmp /var/spool /media /mnt"
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf fuse.glusterfs fuse.sshfs ecryptfs fusesmb devtmpfs"


Thought I'd remove PRUNE_BIND_MOUNTS and try again.

this time I did get it to locate foo but not exactly the results I expected.
There were a bunch of results all like:

/home/.ecryptfs/strycat/.Private/ECRYPTFS_FNEK_ENCRYPTED.FXY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQI-xB3GcuqcZPLq2.6jM-gZo1raJGD.0oJBYQZdOSVPhc-/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIdV3sUJQxDIXjdd0iWhuwzE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIRtwEDc7ZjF0EmHf3xxuPIk--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIsDP2MTSN5RJZrkqikO4AFE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIRtwEDc7ZjF0EmHf3xxuPIk--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIxzNaSr0ExBnirI5DnTtIf---/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIzTC5Kc4nCeLe0uLHYa3Cwk--/ECRYPTFS_FNEK_ENCRYPTED.FXY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIzkT.CrUPB4cPkqNsJVxq8PNUJxxqPBCfooGAL3LEH0k-

There were about a dozen or so results like the above.

What am I doing wrong and how do I fix it?  I did a pretty standard install of kubuntu (however I've since installed xubuntu-desktop and ubuntu-desktop), so it is probably safe to assume that everything still has its default settings.

Edit: I should add locate updatedb.conf finds /etc/updatedb.conf just fine as it does with almost any other file.  It's just files in $HOME that seem to be missing.

---

