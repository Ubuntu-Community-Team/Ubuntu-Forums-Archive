---
title: "updatedb won't index files in $HOME"
date: 2010-08-16
forum: General Help
---

### Post by strycat on 2010-08-16
I thought I posted this earlier today, but it doesn't look like it made it through.

When I do

locate foo

it doesn't find the file foo in /home/strycat  

In fact every file I've tried located in $HOME doesn't seem to be locatable.

So I first did 

sudo updatedb

and tried again.  However I got the same results

So I looked in /etc/updatedb.conf

PRUNE_BIND_MOUNTS="yes"
# PRUNENAMES=".git .bzr .hg .svn"
PRUNEPATHS="/tmp /var/spool /media /mnt"
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf fuse.glusterfs fuse.sshfs ecryptfs fusesmb devtmpfs"

The only thing I thought might be an issue was the PRUNE_BIND_MOUNTS so I commented it out.  Reran updatedb and tried locate again

This time I got some results but not what I expected.  I got about a dozen that looked like:

/home/.ecryptfs/strycat/.Private/ECRYPTFS_FNEK_ENCRYPTED.FXY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQI-xB3GcuqcZPLq2.6jM-gZo1raJGD.0oJBYQZdOSVPhc-/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIdV3sUJQxDIXjdd0iWhuwzE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIRtwEDc7ZjF0EmHf3xxuPIk--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIsDP2MTSN5RJZrkqikO4AFE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIRtwEDc7ZjF0EmHf3xxuPIk--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIxzNaSr0ExBnirI5DnTtIf---/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIzTC5Kc4nCeLe0uLHYa3Cwk--/ECRYPTFS_FNEK_ENCRYPTED.FXY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIzkT.CrUPB4cPkqNsJVxq8PNUJxxqPBCfooGAL3LEH0k-

Obviously that's useless.  So what am I doing wrong and how do I fix it?  I started wtih a default xubuntu install however i have since added kubuntu-desktop and ubuntu-desktop.  Those are the only major non-default packages and settings I've done.

---

### Post by strycat on 2010-08-31
Sorry to bump this, but it has been two weeks and no replies.  Can someone please help?

---

### Post by silverglade00 on 2010-08-31
Ok, let me start by saying that I have never done anything with updatedb or ecryptfs. As in your post is the first time I have encountered them. But I did look at your post for a while to see if I could make sense of it. It looks to me like your home folder is encrypted using ecryptfs. That seems fairly obvious from the /home/.ecryptfs/strycat part of your error messages. 

It looks like the PRUNE stuff is things in the config file that tells updatedb what to skip. So PRUNE_BIND_MOUNTS="yes" tells updatedb to skip bind mounts, whatever they are. I have a feeling it is something like a file system overlay. For example, most of the time your home folder is under /home. But yours is encrypted, so it is under /home/ecryptfs/strycat. This is done invisibly to you so it looks like it is /home/strycat. Sound about right? When you turned off the PRUNE_BIND_MOUNTS by commenting it, I think you told it not to skip file system overlays. 

It looks like it actually found some things, but it can't quite tell what they are. It looks to me that it is because the config is also showing ecryptfs as one of the pruned file systems. 

What I would do is make a backup of the home folder. Probably two to be safe. Then uncomment PRUNE_BIND_MOUNTS. Then remove ecryptfs from PRUNEFS. Then try the updatedb command again.

It seems to me that will fix your issue, but like I said, I don't have any experience with this stuff. Sounds logical to me though.

---

### Post by strycat on 2010-09-02
> **silverglade00 said:**
> 

What I would do is make a backup of the home folder. Probably two to be safe. Then uncomment PRUNE_BIND_MOUNTS. Then remove ecryptfs from PRUNEFS. Then try the updatedb command again.



This worked!  Thanks!

---

